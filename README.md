# LearningCode
Sample Workout
//: A UIKit based Playground for presenting user interface
  
import UIKit
import PlaygroundSupport
//
//class MyViewController : UIViewController {
//    override func loadView() {
//        let view = UIView()
//        view.backgroundColor = .white
//
//        let label = UILabel()
//        label.frame = CGRect(x: 150, y: 200, width: 200, height: 20)
//        label.text = "Hello World!"
//        label.textColor = .black
//
//        view.addSubview(label)
//        self.view = view
//    }
//}
//// Present the view controller in the Live View window
//PlaygroundPage.current.liveView = MyViewController()


enum Grade: CaseIterable {
    
    case a
    case b
    case c
    case e
}

enum Course {
    case physics
    case compute
    case maths
    case chemistry
}

enum Section {
    case one
    case two
    case three
    case four
}

//let sec = Section.one
//
//switch  sec{
//case .one, .two , .three:
//    print("pass")
//default:
//    print("fail")
//}



func checkResult(grade: Grade, course: Course , section: Section) -> String?{
    
    switch (grade, course, section ) {
    case (.e, .maths, .four):
        return "Fail"
    case (.b,  .maths, .three), (.b,  .physics, .three),(.b,  .maths, .four), (.b,  .physics, .four):
        return "First Class in \(course) from \(section)"
    case (.a, .maths, section), (.a, .physics, section):
        return "  Class in \(course) from \(section)"
    case ( .a ,let cou,let sec) where (cou == .compute || cou == .physics) && (sec == .one || sec == .two || sec == .three):
//    case (.a, let course, section):
//        return "Distintnction Class in \(course) from \(section)"
        return "Distinction in \(course) from \(section)"
    case (let grad , let cou, let sec) where [.b, .c].contains(grad) && [.maths, .chemistry].contains(cou) && [.two, .three].contains(sec) :
        
        return "TOpper"
   
    default:
        return nil
    }
    
}

print(checkResult(grade: .c, course: .chemistry, section: .three))



var generateGradeAsCase: ((Grade) -> (String)) {
    
    return { grade in
        
        return "case is \(grade)"
        
    }
}

let generateGradeAsCase2 = { (grade:Grade) -> String in
    return "case is \(grade)"

}

var checkCase:((Grade) -> Bool) {
 return {$0 != .b}
}


let a = Grade.allCases.map{String.init(describing: $0.self)}.joined(separator: "\n")
let b = Grade.allCases.map(generateGradeAsCase)//.joined(separator: "\n")
let c = Grade.allCases.map({ (grade:Grade) -> String in
    return "my case is \(grade)"
})

let d = Grade.allCases.filter { (grade:Grade) -> Bool in
    return grade != .b
}.map(generateGradeAsCase2)

let e = Grade.allCases.filter {
    $0 != .b
    }.map(generateGradeAsCase2)

let f = Grade.allCases.filter(checkCase).map(generateGradeAsCase2)

print(a)
print(b)

print(c)
print(d)
print(e)
print(f)

// b ||  c ,   phy || chem || math  , two || three


