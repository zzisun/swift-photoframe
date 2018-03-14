## 미션 진행사항
### Step1 - 시작하기 - Tabbed App 템플릿
#### viewDidLoad()
- Question: 자동 생성된 ViewController 클래스 viewDidLoad() 함수에서 print(#file, #line, #function, #column) 코드를 추가하고 실행하면 콘솔 영역에 무엇이 출력되는지 확인한다.
- Answer: 2018.03.09 16:50
  ![screenshot_step1_viewDidLoad](./Screenshot/screenshot_step1_viewDidLoad.png)
#### UITabBarController 와 UITabBar
- Question: 애플 UIKit View Management 클래스 중에서 UITabBarController 와 UITabBar에 대해 학습한다.
- Answer: [UITabBarController 와 UITabBar에 대한 내용 정리 링크](https://jinios.github.io/ios/2018/03/09/difference_UITabBar_UITabBarController/)

### Step2 - IBOutlet
> Assistant Editor Mode에서 레이블을 선택하고 `control + 드래그`로 ViewController 코드에 IBOutlet으로 연결한다.

- 구현 화면: 2018.03.11 19:20
  ![screenshot_step2_IBOutlet](./Screenshot/screenshot_step2_IBOutletProperty.png)

#### UILabel 클래스 속성 (계속 추가할 예정)
  - `vat text: String? { get set }`
  - `var textColor: UIColor! { get set }`
    - [Custom textColor를 사용하는 방법 정리](https://jinios.github.io/ios/2018/03/11/ios_color_literal/)
  - `var font: UIFont! { get set }`
    - font속성 사용예시 : `labelName.font = labelName.font.withSize(15)`

### UI
User Interface의 약자로, 사용자와 직접 상호작용 하는 접점을 뜻한다. 모바일 앱 개발에서는 사용자가 보는 화면이라고 생각하면 됨.

#### Interface Builder & Storyboard
***Interface Builder:*** Xcode에서, 앱의 UI요소들을 visualized해서 컨트롤 할 수 있도록 해주는 인터페이스 빌더.

***Storyboard:*** device상에서 사용자에게 나타나는 UI를 보여주는 파일. <br/>템플릿으로부터 만들어진 모든 프로젝트들은 Main.storyboard파일과 iOS앱의 경우 LaunchScreen.storyboard파일이 있다.(앱이 런칭될 때 화면) 이 스토리보드 파일은 뷰컨트롤러와 뷰를 가지고있는데 스토리보드 파일 내의 UI요소들을 확인하면서 인터페이스 빌더를 통해 이를 변경/확인할 수 있다.

#### IBOutlet과 IBAction의 관계
![screenshot_step2_IBOutlet_IBAction](./Screenshot/step2_IBOutlet_IBAction.png)

- ***IBOutlet과 IBAction:***
  - 화면(View)와 컨트롤러를 연결하고 매핑시키는 작업을 할 때 사용한다.
  - 사용자는 View와 상호작용한다.
  - IBAction은 사용자를 통해 발생한 이벤트를 감지해서 Controller에 메시지를 보낸다.
  - 컨트롤러는 특정 로직을 수행하고 뷰에 변경사항이 있으면 어떤 것을 변경하라는 지시를 내린다.
  - IBOutlet은 처리 결과를 View단에 알려서 원하는 동작을 이끌어낸다.


`IBOutlet(ex. 코드와 연결된 버튼) -> 코드는 그 버튼을 조정할 수 있게 됨 -> IBAction(버튼을 동작시켰을때 어떻게 변화해야하는지에 대한 동작을 담고있는 메소드)`
스토리보드에 있는 UI요소들과 연결하고싶은 속성을 코드로 정의했다면 아래의 키워드를 이용해서 연결시킬 수 있다.
  - ***IBOutlet :***
  인터페이스 빌더에서 사용되는 타입 한정자로, 코드가 UI 엘리먼트에 메시지를 보낼 수 있도록 하기 위한 연결점같은 개념이다. 속성이나 객체변수를 선언할때 객체 변수의 앞에 쓴다.
    ```swift
    @IBOutlet weak var photoLabel: UILabel!
    ```
  - ***IBAction:***
  인터페이스 빌더에서 사용되는 타입 한정자로, 메소드를 UI 엘리먼트와 코드 간의 연결점해주기 위한 개념이다. 메소드 선언 시 `void` 리턴타입 대신 사용한다.
    ```swift
    @IBAction func likedThis(sender: UIButton) {
      ...
    }
    ```
  [IBOutlet과 IBAction 참고링크](https://thatthinginswift.com/ibaction-and-iboutlet/)


### Step3 - IBAction
> First Scene에 버튼(UIButton)을 추가하고 IBAction으로 연결한다.

- 구현화면 : 2018.03.12 14:30
  - 버튼 클릭 전
    ![screenshot_step2_IBOutlet](./Screenshot/step3_beforeAction.png)
  - 버튼 클릭 후
    ![screenshot_step2_IBOutlet](./Screenshot/step3_afterAction.png)


#### 버튼에 IBAction을 추가할 때 이벤트(Event) 종류
![screenshot_step2_IBOutlet](./Screenshot/step3_sentEvents.png)

- touchDown
  - A touch-down event in the control.

- touchDownRepeat
  - A repeated touch-down event in the control; for this event the value of the UITouch tapCount method is greater than one.

- touchDragInside
  - An event where a finger is dragged inside the bounds of the control.

- touchDragOutside
  - An event where a finger is dragged just outside the bounds of the control.

- touchDragEnter
  - An event where a finger is dragged into the bounds of the control.

- touchDragExit
  - An event where a finger is dragged from within a control to outside its bounds.

- touchUpInside
  - A touch-up event in the control where the finger is inside the bounds of the control.

- touchUpOutside
  - A touch-up event in the control where the finger is outside the bounds of the control.

- touchCancel
  - A system event canceling the current touches for the control.

- valueChanged
  - A touch dragging or otherwise manipulating a control, causing it to emit a series of different values.

- primaryActionTriggered
  - A semantic action triggered by buttons.

- editingDidBegin
  - A touch initiating an editing session in a UITextField object by entering its bounds.

- editingChanged
  - A touch making an editing change in a UITextField object.

- editingDidEnd
  - A touch ending an editing session in a UITextField object by leaving its bounds.

- editingDidEndOnExit
  - A touch ending an editing session in a UITextField object.

#### 버튼에 액션을 여러개 추가할 수 있을까?
  - 연결은 가능하지만, 메소드 내부에서 절차적으로 실행되기때문에 결과적으로 view에는 가장 마지막 코드만 적용되어 보여지게된다.
#### 버튼이 여러일 때 하나의 액션에 추가할 수 있을까?
  - 하나의 메소드를 재활용이 가능한 구조로 설계하여 여러 객체에 사용하게 만들 수 있는 것처럼 마찬가지로 여러 IBOutlet과 연결이 가능하지만, 만약 IBOutlet의 종류마다 다르게 동작하도록 만들고싶다면 IBAction메소드 내부에서 `switch-case`를 사용해서 만들 수 있다. [(참고링크)](https://stackoverflow.com/questions/37870701/how-to-use-one-ibaction-for-multiple-buttons-in-swift)


### Step4 - Scene과 Segue
> 스토리보드 구성 요소에 대해 학습하고 새로운 Scene과 Segue를 추가한다.

- 구현 화면 2018.03.13 14:10
![screenshot_step4-1](./Screenshot/step4_first.png)
![screenshot_step4-2](./Screenshot/step4_second.png)
![screenshot_step4-3](./Screenshot/step4_third.png)
### Segue
Segue는 앱 인터페이스의 흐름이다. 즉 segue는 앱의 스토리보드 파일에서 두개의 뷰 컨트롤러 간 변환되는 과정 자체를 나타낸다고 볼 수 있다. Segue의 시작점을 버튼이나 table row, 또는 segue를 동작하게 하는 제스쳐이고, 종료지점은 보여주고 싶은 뷰 컨트롤러이다.
Segue는 항상 새로운 뷰 컨트롤러를 보여주지만 unwind segue를 이용하여 뷰 컨트롤러를 보이지 않게(화면에서 없어지게- 만약 현재 뷰 컨트롤러를 보이지 않게 만들때, 새로운 뷰 컨트롤러를 덮어서 안보이게 하는 것이 아니라 현재 뷰를 화면에서 없앰으로서) 만들 수 있다.
[참고링크](https://developer.apple.com/library/content/featuredarticles/ViewControllerPGforiPhoneOS/UsingSegues.html)

![screenshot_step4-segueObject](./Screenshot/step4_segueObject.png)


### Segue action

***Show*** - Pushes the destination view controller onto the navigation stack, sliding overtop from right to left, providing a back button to return to the source - or if not embedded in a navigation controller it will be presented modally
Example: Navigating inboxes/folders in Mail

***Show Detail*** - For use in a split view controller, replaces the detail/secondary view controller when in an expanded 2 column interface, otherwise if collapsed to 1 column it will push in a navigation controller
Example: In Messages, tapping a conversation will show the conversation details - replacing the view controller on the right when in a two column layout, or push the conversation when in a single column layout

***Present Modally*** - Presents a view controller in various animated fashions as defined by the Presentation option, covering the previous view controller - most commonly used to present a view controller that animates up from the bottom and covers the entire screen on iPhone, or on iPad it's common to present it as a centered box that darkens the presenting view controller
Example: Selecting Touch ID & Passcode in Settings

***Popover Presentation*** - When run on iPad, the destination appears in a popover, and tapping anywhere outside of this popover will dismiss it, or on iPhone popovers are supported as well but by default it will present the destination modally over the full screen
Example: Tapping the + button in Calendar

***Custom*** - You may implement your own custom segue and have control over its behavior

#### Segue and IBAction
Segue 객체를 만들고 IBAction과 연결 할 수 있다. 스토리보드에서 연결하고자 하는 시작점의 view와 도착점의 view를 `control + 드래그`로 연결해서 segue를 만든다.
![screenshot_step4-5](./Screenshot/step4-viewcontroller_segue.png)
시작점의 ViewController코드에서 아래와 같이 `performSegue()`메소드를 사용한다.
```swift
  @IBAction func moveToNavy(_ sender: Any) {
     performSegue(withIdentifier: "toNavy", sender: self)
  }
```
- 파라미터 `withIdentifier:`는 스토리보드에서 segue를 만들고 Attributes Inspector에서 identifier로 설정해준 문자열을 입력하면 된다.
![screenshot_step4-3](./Screenshot/step4-segue-identifier.png)
[참고링크](https://www.youtube.com/watch?v=WfT-hJXuiys)

### Step5 - ViewController 프로그래밍
> 스토리보드 구성 요소와 클래스 코드와 연결해서 동작을 확장한다.

- 구현 화면 : 2018.03.13 19:00
- FirstViewController > BlueViewController > NavyViewController > FirstViewController
- ![screenshot_step5-1](./Screenshot/step5-1.png)
- ![screenshot_step5-2](./Screenshot/step5-2.png)
- ![screenshot_step5-3](./Screenshot/step5-3.png)
- ![screenshot_step5-4](./Screenshot/step5-4.png)


### 뷰 생명주기
뷰 생명주기의 기본 flow는
- ***viewDidLoad > viewWillAppear > viewDidAppear > viewWillDisappear > viewDidDisappear***
(단, viewDidLoad는 rootView이기때문에 한번만 호출되는 것이 일반적이다. [참고링크](http://zeddios.tistory.com/43))

FirstView - BlueView - NavyView - FirstView로 연결된 flow일때, `print(#file, #line, #function, #column)`로 콘솔에 표시
```
.../FirstViewController.swift 27 viewDidLoad() 40 >> 첫번째 뷰 로드
.../FirstViewController.swift 48 viewWillAppear 40 >> 첫번째 뷰가 보일 것이다.
.../FirstViewController.swift 52 viewDidAppear 40 >> 첫번째 뷰가 보임.  
------- 버튼 터치 ------- (FirstView -> BlueView)
.../BlueViewController.swift 15 viewDidLoad() 40 >> 첫번째 뷰에서 다음버튼 터치 순간실행. BlueViewController 차례시작, 다음(blue)뷰가 로드되고
.../FirstViewController.swift 56 viewWillDisappear 40 >> 이전(first)뷰가 사라질 준비
.../BlueViewController.swift 28 viewWillAppear 40 >> 다음 뷰가 로드될 준비
.../BlueViewController.swift 32 viewDidAppear 40 >> 다음 뷰 나타남
.../FirstViewController.swift 60 viewDidDisappear 40 >> 이전 뷰 사라짐
------- 버튼 터치 ------- (BlueView -> NavyView)
.../NavyViewController.swift 15 viewDidLoad() 40 >> BlueView에서 다음 버튼 터치 순간실행. NavyView차례 시작. NavyView 로드
.../BlueViewController.swift 45 viewWillDisappear 40 >> BlueView는 사라질 예정
.../NavyViewController.swift 32 viewWillAppear 40 >> NavyView가 나타날 준비
.../NavyViewController.swift 36 viewDidAppear 40 >> NavyView가 나타남
.../BlueViewController.swift 49 viewDidDisappear 40 >> BlueView 사라짐
------- 버튼 터치 ------- (NavyView -> FirstView)
.../FirstViewController.swift 27 viewDidLoad() 40 >> FirstView 로드
.../NavyViewController.swift 40 viewWillDisappear 40 >> NavyView가 사라질 예정
.../FirstViewController.swift 48 viewWillAppear 40 >> FirstView가 나타날 준비
.../FirstViewController.swift 52 viewDidAppear 40 >> FirstView가 나타남
.../NavyViewController.swift 44 viewDidDisappear 40 >> NavyView 사라짐

```
- **중요** : 다음`(Next)`뷰는 이전`(Previous)`뷰가 사라진 다음에 나타나는 것이 아니라, **다음 뷰가 나타나고(viewDidAppear) 그 이후에 이전 뷰가 사라진(viewDidDisappear)다!**
- **비교** : 앞서말한 [참고링크](http://zeddios.tistory.com/43)의 설명과 달리 FirstViewController가 NavyViewController로부터 재호출 될때 viewDidLoad가 한번 더 호출 된 이유는, FirstViewController를 호출할때 `instantiateViewController(withIdentifier:)`를 사용했기 때문인 것 같다. <br/>이 메서드는 호출하고싶은 뷰 컨트롤러의 인스턴스를 호출할때마다 만든다는 특징이 있다.(This method creates a new instance of the specified view controller each time you call it. [참고](https://developer.apple.com/documentation/uikit/uistoryboard/1616214-instantiateviewcontroller))


### 콜백함수
- 사용자에 의해 호출되는 것이 아닌 특정 함수에서 호출돼 필요시 코드 내에서 사용되는 함수.
- 호출된 함수를 알려주어, 다른 프로그램 또는 다른 모듈에서 함수를 호출 하게 하는 방법


### Step6 - Container ViewController

스토리보드에서 First Scene을 선택하고, Editor > Embed In > Navigation Controller 항목을 선택한다. - FirstScene을 루트 뷰 컨트롤러로 설정(UINavigationController를 초기화할때 인스턴스에 UIVIewController를 전해줘야하는데, 이 UIVIewController가 내비게이션 컨트롤러의 viewControllers 배열에 추가되고, 루트 뷰 컨트롤러가 된다.)

#### UINavigationController
> 스택, 뷰 컨트롤러의 배열을 가진다

- 내비게이션 컨트롤러가 있을 경우와 없을 경우 화면 전환 동작이 어떻게 다른지, 화면들 포함관계가 있는지 학습한다.
- 내비게이션 컨트롤러 관련 메서드가 왜 push / pop 인지 학습한다.

![screenshot_step5-1](./Screenshot/step6-UINavigationController-diagram.png)

항상 두 개의 하위 뷰를 가지는데, UINavigationBar와 topViewController의 view다.
스택 구조로 뷰 컨트롤러를 가지기 때문에, push, pop단어가 메서드 이름에 들어간다.
뷰 컨트롤러가 스택에 푸시되면 컨트롤러의 view가 우측에서부터 미끄러지듯이 화면에 나타난다.
스택이 팝 될때는 (마지막 항목, 스택의 맥 위의 - presenting 뷰 컨트롤러가 제거) view는 우측으로 사라진다. 즉 topViewController의 view가 사용자에게 보여지는 것이다.


#### Issue: close 버튼에 추가한 함수 에러
> popViewController()

close 버튼을 누르면 previous 뷰가 나오듯이 동작해야 함? 아래 애플문서에 기재된 글처럼 rootView를 pop하려고 해서 나는 에러는 아닌것 같다.
This method removes the top view controller from the stack and makes the new top of the stack the active view controller. If the view controller at the top of the stack is the root view controller, this method does nothing. In other words, you cannot pop the last item on the stack. - 루트 뷰는 pop할 수 없다.

- 콘솔에 뜬 에러 내용 : 첫번째 화면 > Next > light-blue 화면에서 close 터치 시 발생
```
2018-03-14 15:46:53.764490+0900 PhotoFrame[15032:176458] -[PhotoFrame.BlueViewController closeButtonClicked:]: unrecognized selector sent to instance 0x7fa956429ca0
2018-03-14 15:46:53.934517+0900 PhotoFrame[15032:176458] *** Terminating app due to uncaught exception 'NSInvalidArgumentException', reason: '-[PhotoFrame.BlueViewController closeButtonClicked:]: unrecognized selector sent to instance 0x7fa956429ca0'
*** First throw call stack:
(
	0   CoreFoundation                      0x0000000104b4612b __exceptionPreprocess + 171
	1   libobjc.A.dylib                     0x0000000100db9f41 objc_exception_throw + 48
	2   CoreFoundation                      0x0000000104bc7024 -[NSObject(NSObject) doesNotRecognizeSelector:] + 132
	3   UIKit                               0x0000000101889f51 -[UIResponder doesNotRecognizeSelector:] + 295
	4   CoreFoundation                      0x0000000104ac8f78 ___forwarding___ + 1432
	5   CoreFoundation                      0x0000000104ac8958 _CF_forwarding_prep_0 + 120
	6   UIKit                               0x0000000101657972 -[UIApplication sendAction:to:from:forEvent:] + 83
	7   UIKit                               0x00000001017d6c3c -[UIControl sendAction:to:forEvent:] + 67
	8   UIKit                               0x00000001017d6f59 -[UIControl _sendActionsForEvents:withEvent:] + 450
	9   UIKit                               0x00000001017d5e86 -[UIControl touchesEnded:withEvent:] + 618
	10  UIKit                               0x00000001016cd807 -[UIWindow _sendTouchesForEvent:] + 2807
	11  UIKit                               0x00000001016cef2a -[UIWindow sendEvent:] + 4124
	12  UIKit                               0x0000000101672365 -[UIApplication sendEvent:] + 352
	13  UIKit                               0x0000000101fbea1d __dispatchPreprocessedEventFromEventQueue + 2809
	14  UIKit                               0x0000000101fc1672 __handleEventQueueInternal + 5957
	15  CoreFoundation                      0x0000000104ae9101 __CFRUNLOOP_IS_CALLING_OUT_TO_A_SOURCE0_PERFORM_FUNCTION__ + 17
	16  CoreFoundation                      0x0000000104b88f71 __CFRunLoopDoSource0 + 81
	17  CoreFoundation                      0x0000000104acda19 __CFRunLoopDoSources0 + 185
	18  CoreFoundation                      0x0000000104accfff __CFRunLoopRun + 1279
	19  CoreFoundation                      0x0000000104acc889 CFRunLoopRunSpecific + 409
	20  GraphicsServices                    0x00000001072bf9c6 GSEventRunModal + 62
	21  UIKit                               0x00000001016565d6 UIApplicationMain + 159
	22  PhotoFrame                          0x00000001004980e7 main + 55
	23  libdyld.dylib                       0x0000000105cddd81 start + 1
	24  ???                                 0x0000000000000001 0x0 + 1
)
libc++abi.dylib: terminating with uncaught exception of type NSException
(lldb)
```

#### firstTab과 secondTab을 전환할때 콜백함수 호출 변화
 
