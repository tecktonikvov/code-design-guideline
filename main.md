# Ласкаво просимо!

У нашій Swift команді ми дотримуємося встановлених правил та стандартів написання коду, які допомагають підтримувати його чистим, зрозумілим та легким для подальшого розвитку. Основною метою наших принципів є забезпечення єдиного підходу до написання коду, що сприяє кращій командній взаємодії та мінімізує ризики, пов’язані з несумісністю.

# Для кого призначені ці правила?

Ці правила призначені для всіх розробників, які працюють над проєктом, незалежно від їхнього досвіду чи ролі в команді. Вони допомагають:

1. **Новим членам команди**: Швидше адаптуватися до стилю написання коду в проєкті, зрозуміти структуру та підходи до розробки.
2. **Досвідченим розробникам**: Забезпечити єдиний підхід до написання коду і спростити код-рев'ю.
3. **Командам, які підтримують проєкт**: Зробити код більш зрозумілим і легким для підтримки, особливо при масштабуванні проєкту.
4. **Контрактним розробникам**: Полегшити інтеграцію їхнього внеску в основний код проєкту завдяки зрозумілим стандартам.
5. **Усім, хто читає код**: Зменшити когнітивне навантаження за рахунок використання зрозумілого і послідовного стилю написання.

Дотримання цих правил дозволяє підвищити якість коду, сприяє кращій співпраці в команді та забезпечує довготривалу підтримку проєкту.

### Переваги використання єдиного кодстайлу:

- **Зрозумілість**: Уніфікований стиль спрощує читання та розуміння коду всіма членами команди.
- **Легкість підтримки**: Код, написаний за загальними правилами, простіше підтримувати та розвивати в майбутньому.
- **Зниження помилок**: Завдяки дотриманню стандартів зменшується кількість технічних помилок і конфліктів.
- **Ефективність**: Уніфіковані підходи до структуризації та стилю дозволяють зекономити час на рев’ю та інтеграцію коду.
- **Командна згуртованість**: Спільний стиль сприяє кращій взаємодії всередині команди та швидшому залученню нових учасників.

Ознайомтеся з цими правилами перед початком роботи, щоб ваш внесок став важливою частиною успіху нашого проєкту.

# Кілька важливих правил, які варто пам’ятати:

1. **Читабельність і ясність — головна мета.**  
   Код пишуть значно рідше, ніж читають або використовують в інших місцях. Вибравши правильне ім’я для методу чи змінної один раз, ви спрощуєте їх розуміння іншими розробниками.

2. **Ясність завжди має пріоритет над стислістю.**  
   Незважаючи на те, що в Swift можна писати дуже короткий код, це не повинно бути самоціллю. Назви змінних, методів і класів завжди мають відображати їхнє призначення, навіть якщо це робить їх довшими.

Дотримуючись цих принципів, ви допоможете зробити код вашої команди більш зрозумілим і зручним у роботі.

# Іменування та правила проектування API

Іменування змінних, класів, методів та іх аргументів є одним із ключових правил під час написання будь-якого коду. Коли члени команди керуються спільними правилами іменування, можна сказати, що вони "говорять однією мовою". Це полегшує розуміння коду під час його читання, а також сприяє ефективній комунікації між розробниками.

### Підходи до іменування та правила проектування API:

- **[ENG Swift API Design Guidelines](https://swift.org/documentation/api-design-guidelines/)**  
- **[RU Swift API Design Guidelines](https://github.com/tecktonikvov/code-design-guideline/blob/main/Swift%20API%20design%20guidelines.pdf)**

# Префікси класів

Ми не використовуємо префікси для класів якщо це можливо.

Swift автоматично додає префікси до назв класів (за назвою модуля), тому ситуації, коли два класи з однаковими назвами конфліктують, виключені. Якщо ж виникає конфліктна ситуація, можна використати назву модуля, щоб явно вказати, який клас слід використовувати:

```swift
import SomeModule

let service: SomeModule.Service
```

# Декларування об'єктів

При оголошенні об'єктів (класи, протоколи) між назвою та початком блоку не робиться перенесення рядка:

```swift
final class Formatter {
    var definition
}
```

# Декларування властивостей

1. **Властивості згруповані:**
	1. Статичні властивості
	1. Cпеціальні модифікатори, які починаються з @ (@IBOutlet, @objc, e.t.c)
	1. Не статичні властивості

1. **Усередині кожної групи властивості сортуються:**
	1. За строгістю зони видимості (від private до open).
	1. За кількістю символів (від коротшого до довшого).
	1. За алфавітом (за зростанням).

2. **Групи:**
   - Групи повинні бути розділені вертикальними відступами.
    
    
- Властивості всередині кожної групи повинні слідувати правилу кількості символів та алфавітного порядку.
- Властивості всередині кожної групи не повинні бути розділені вертикальними відступами.
  Вийняком становлять обчислювальні властивості. Ці властивості завжди розділяються вертикальним відступом.
 
 ```swift
var someInt: Int {
    // Some logic
}
	
var someBool: Bool {
    // Some logic
}
```

### Приклад

```swift
final class Example {
   private static let someStaticPrivateConstant: CGFloat = 16.0
   
   static let shared = Example()
   static let someStaticConstant: CGFloat = 16.0
   
   @IBOutlet weak private var titleLabel: UILabel!
   @IBOutlet weak private var backButton: UIButton!
   @IBOutlet weak private var containerView: UIView!

   private let lessSymbolsProperty: Int
   private let aLittleBitMoreSymbolsProperty: String
   private let theMostLongerSymbolsProperty: SomeCustomType1
   	
   private(set) var firstPrivateSetVar: Int
   private(set) var secondPrivateSetVar: Int
	
   var firstBool: Bool
   var secondBool: String
	
   public lazy var firstLazyVar: Bool
   public lazy var secondLazyVar: String
	
   weak var firstWeakVariable: SomeCustomType2?
   weak var secondWeakVariable: SomeCustomType3?
	
   var firstComputedVariable: Int {
      // Some logic
   }
	
   var secondComputedVariable: Int {
      // Some logic
   }
	
   public publicFirstVariable: String
   public publicsecondVariable: String
	
   open openFirstVariable: String
   open openSecondVariable: String
}
```

# Readonly
Якщо властивість об'єкта повинна бути доступна лише для читання, використовується модифікатор **private(set)**

```swift
final class Weather {
   private(set) var temperature: Temperature
}
```

Якщо ж властивість задається під час ініціалізації об'єкта і не змінюється надалі, використовується **let**

```swift
final class Request {
   let timeout: TimeInterval

   init(timeout: TimeInterval) {
      self.timeout = timeout
   }
}
```

# Модифікатори видимості
Модифікатори області видимості всередині класів мають пріоритет у написанні (розташовуються першими):

```swift
final class Example {
    private let constant = 10.0
    private(set) var isReadonly = true
    fileprivate final lazy var alwaysTrue = true

    private func foo() {
        // Some logic
    }
}
```

Винятком є спеціальні модифікатори, які починаються з @:

```swift
final class Example {
    @objc let constant = 10.0
    @IBOutlet private(set) var titleLabel: UILabel!
    @IBAction private func cancelButtonClicked(sender: UIButton) {
    	// Some logic
    }
}
```

# Винесення до Constants

Для покращення читабельності та підтримки коду рекомендується виносити у **Constants**:

1. **Налаштування об'єктів**, які не можуть бути виконані у місці їхньої декларації:
   - Якщо для налаштування потрібні дані, що недоступні під час ініціалізації.
   - Це стосується, наприклад, значень відступів, розмірів, шрифтів тощо.

2. **Ідентифікатори та ключі**, які використовуються для доступу до елементів інтерфейсу або конфігурацій:
   - Назви кнопок, ярликів, ключів для `UserDefaults` тощо.

3. **Повторювані значення**, які використовуються у кількох місцях:
   - Наприклад, константи для кольорів, шрифтів, значень відступів і розмірів.

#### Що не варто виносити у Constants:
- **Глобальні значення, які не повторюються у коді.** 
  - Наприклад, якщо певне значення використовується лише один раз у межах методу або класу, його немає сенсу додавати до **Constants**.
- **Значення, які є локальними для невеликих функцій або методів.** 
  - Такі константи можна оголошувати локально в межах функції для збереження контексту.

#### Виняток:
- Якщо значення використовується кілька разів навіть у межах одного класу, його варто винести у **Constants**, щоб уникнути дублювання.

#### Переваги використання Constants:
- **Зручність підтримки:** Усі налаштування зосереджені в одному місці.
- **Прозорість:** Легше зрозуміти, як налаштовуються об'єкти.
- **Гнучкість:** Швидко змінювати значення в одному місці без необхідності проходити весь код.
- **Уникнення дублювання:** Один раз визначене значення використовується в кількох місцях.

#### Приклад використання:

```swift
final class SomeViewController: UIViewController {
    private let button = UIButton()
    private let separatorView = UIView()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        setupUI()
    }
    
    private func setupUI() {
        button.layer.cornerRadius = Constants.cornerRadius
        button.heightAnchor.constraint(equalToConstant: Constants.buttonHeight).isActive = true
        
        separatorView.heightAnchor.constraint(equalToConstant: Constants.separatorHeight).isActive = true
    }
}

// MARK: - Constants
private enum Constants {
    static let cornerRadius: CGFloat = 16.0
    static let spacing: CGFloat = 20.0
    static let buttonHeight: CGFloat = 58.0
    static let separatorHeight: CGFloat = 2.0
    static let closeButtonIdentifier = "btn_white_close"
}
```

### Рекомендація:
- Використовуйте private enum Constants із файловою зоною видимості.
- Розташовуйте секцію Constants в кінці файлу для підтримки структурованості.
- Константи мають бути статичними (static) для уникнення зайвих екземплярів.
- Не додавайте в Constants значення, які використовуються лише один раз, за винятком випадків, коли це покращує читабельність або дозволяє уникнути дублювання.


# Декларування та налаштування вкладених об'єктів
Поширеною практикою є **"лінива ініціалізація з використанням замикання" (lazy initialization using a closure)**.
Декларування об'єкта та його початкові налаштування відбуваються у одному місці у середині кложури.

**Приклад:**

```swift
final class ParentObject {
    private let jsonDecoder: JSONDecoder = {
        let decoder = JSONDecoder()
        decoder.allowsJSON5 = true
        decoder.dateDecodingStrategy = .secondsSince1970
        return decoder
    }()
}
```

**Переваги:**

1. Чистота коду: 
	* Ініціалізація та налаштування об'єкта виконуються в одному місці.
2. Зручність:
	* Дозволяє уникнути перевантаження ініціалізатора.
3. Зрозумілість: 
	* Якщо налаштування об'єкта складне, воно структуроване та ізольоване.

# Логічне структурування коду (TBD)
Для покращення читабельності коду, рекомендується розділяти логічні кроки у методах чи функціях вертикальними відступами (порожніми рядками). Це допомагає швидше зрозуміти структуру коду, виділяючи окремі блоки виконання.

**TBD: Тут думки розділяются 
Перший варіант це те як описано, другий це не робити відступи в скоупах методів взагалі що б виділяти методи візуально було легше, або робити 1 відступ у ускоупі методів та 2 перед оголошенням методів.**

### **Правила використання вертикальних відступів:**
1. **Виділення логічних блоків:**
   - Розділяйте код на зрозумілі секції, наприклад:
     - Ініціалізація змінних.
     - Виклик методів.
     - Обробка результатів.
     - Повернення значень.

2. **Не залишайте надмірну кількість порожніх рядків:**
   - Використовуйте **один** порожній рядок між логічними блоками, щоб уникнути "розриву" структури.

3. **Не залишайте порожні рядки перед закриваючими дужками `}`:**
   - Це порушує загальний стиль та виглядає як помилка.

### **✅ Приклад правильного оформлення:**

```swift
let apiClient = APIClient()

func fetchUserData() -> User? {
    let request = UserRequest()

    guard let response = apiClient.perform(request) else {
        return nil
    }

    let user = User(data: response.data)

    return user
}
```

### **❌ Приклад неправильного оформлення:**

```swift
func fetchUserData() -> User? {
    let apiClient = APIClient()
    let request = UserRequest()
    guard let response = apiClient.perform(request) else {
        return nil
    }
    let user = User(data: response.data)
    return user
}
```

Дотримання цього правила допомагає швидше орієнтуватися в коді, виділяючи основні кроки виконання, та полегшує його підтримку і рев'ю.

# Використання `return`
Хоча swift і дозволяе не писати return щось повертается зі скоупу та вираз займае 1 рядок, треба явно повертати якісь занчення використовуючи return.
Цей підхід забезпечує однорідність коду, оскільки всі методи використовують явне повернення.

#### **Приклад:**

```swift
func square(of number: Int) -> Int {
    return number * number
}
```

# Загальна структура файлу
Чітка структура файлу сприяє легшому розумінню, навігації та підтримці коду. У файлах рекомендується дотримуватися певного порядку розміщення елементів, щоб забезпечити єдиний підхід до організації коду в команді.


### **Рекомендований порядок:**
1. **Імпорти:**
   - Імпорти розташовані за кількістю символів, а потім алфавітом

   ```swift
    import UIKit
    import Alamofire
    import Foundation
    import MyApplicationCore
	```
	
	або (TBD)
	
   - Спочатку імпортуються стандартні бібліотеки.
   - Потім імпортуються сторонні фреймворки та модулі.
   - Завершується імпорт внутрішніх модулів проєкту.
   - Між групами імпортів використовуйте порожній рядок.

   ```swift
    import UIKit
    import Foundation

    import Alamofire

    import MyAppCore
   ```
   
2. **Декларування класу/структури/протоколу:**
	- Назва класу або іншої сутності одразу йде після імпортів.
	- За потреби додається документація.

3. **Властивості:**
	- Розміщуються на початку класу для легкого доступу та читабельності.
	- Більш детально описано у главі **"Декларування властивостей"**
	
4. **Ініціалізатори:**
	- `init` розміщується одразу після констант та статичних властивостей.
	- Ініціалізатори мають бути компактними та зрозумілими.

5. **Методи:**
	- Методи життевого циклу розміщується одразу після констант ініціалізаторів.
	- Інші методи поділяются на групи за модифікатором доступу (публічні, внутрішні, приватні). В середині групи за типом (геттери, сеттери, мережеві запити, фабричні методи, службові)
	- Одразу після методів життевого цикл розташовуются статичні методи, потім усі інші.

	**TBD: Чи треба розташовувати статичні методи разом із статичними змінними у початку класу/стурктури?**
	- Усі методи відсортовані за модифікатором доступу (від open до private).
	- @objc методи у кінці.
6. **Розширення (Extensions):**
	- Якщо файл містить кілька розширень для класу/структури, вони розташовуються в кінці файлу. Окрім випадків коли основна або єдина задача це виконувати вимоги протоколу, у цьому випадку можна вказувати протокол після назви об'єкта. А методи протоколу які реалізуе цей об'єкт повинні бути відокремлені за допомогою `// MARK:`
	- Спочатку слід розташовувати розширення із стандартної бібліотеки apple: UITableViewDelegate, UITextFieldDelegate, e.t.c.
	- Наступними слід розташовувати кастомні розширення: UserManagerDelegate, e.t.c.
	- Останніми розширення базових класів.

7. **Службові типи:**
	- Невеликі пов'язані допоміжні типи можуть бути визначені в одному файлі. Це може бути корисно при використанні fileprivate для обмеження певної функціональності типу та/або його допоміжними типами тільки в цьому файлі.
	- Місце декларації службових типів слід вибирати самостійно, з урахуванням зручності їх використання та читабельності коду. 

### Приклад:

```swift
import UIKit
import MyApplicationCore

protocol ExampleOfProtocol {
    func doSomething()
}

struct ExampleViewControllerDataModel {
    let isWarning: Bool
    let title: String
    let description: String
}

/// View controller that shows an example of code style usage
final class ExampleViewController: UIViewController {
    static let subtitleLabelFontSize: CGFloat = 24.0

    @IBOutlet private weak var titleLabel: UILabel!
    
    // MARK: - Properties
    private let subtitleLabel: UILabel = {
        let label = UILabel()
        label.numberOfLines = 0
        label.font = .systemFont(ofSize: subtitleLabelFontSize)
        label.textAlignment = .center
        label.translatesAutoresizingMaskIntoConstraints = false
        return label
    }()
    
    private lazy var mainButton: UIButton = {
        let button = UIButton()
        button.layer.cornerRadius = 12
        button.backgroundColor = .systemBlue
        button.translatesAutoresizingMaskIntoConstraints = false
        button.addTarget(self, action: #selector(onMainButtonTap), for: .touchUpInside)
        return button
    }()
    
    private lazy var textField: UITextField = {
        let textField = UITextField()
        textField.borderStyle = .roundedRect
        textField.translatesAutoresizingMaskIntoConstraints = false
        textField.delegate = self
        return textField
    }()
    
    private let descriptionView: DescriptionView = {
        let _descriptionView = DescriptionView()
        _descriptionView.layer?.cornerRadius = 12
        _descriptionView.layer?.cornerCurve = .continuous
        _descriptionView.translatesAutoresizingMaskIntoConstraints = false
        return _descriptionView
    }()
    
    // MARK: - Init
    init() {
        super.init(nibName: nil, bundle: nil)
        setup()
    }
    
    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }
    
    // MARK: - Lifecycle
    override func viewDidAppear(_ animated: Bool) {
        super.viewDidAppear(animated)
        runApperanceAnimation()
    }

    // MARK: - Private
    private func setup() {
        view.backgroundColor = .white
        
        setupTitleLabel()
        setupSubtitleLabel()
        setupDescriptionView()
        setupTextField()
        setupMainButton()
    }
    
    private func setupTitleLabel() {
        titleLabel.font = Constants.titleFont
        titleLabel.numberOfLines = 0
        
        view.addSubview(titleLabel)
        NSLayoutConstraint.activate([
            // ...
        ])
    }

    private func setupSubtitleLabel() {
        view.addSubview(subtitleLabel)
        NSLayoutConstraint.activate([
            // ...
        ])
    }
    
    private func setupDescriptionView() {
        view.addSubview(descriptionView)
        NSLayoutConstraint.activate([
            // ...
        ])
    }
    
    private func setupTextField() {
        view.addSubview(textField)
        NSLayoutConstraint.activate([
            // ...
        ])
    }
    
    private func setupMainButton() {
        view.addSubview(mainButton)
        NSLayoutConstraint.activate([
            // ...
        ])
    }
    
    private func runApperanceAnimation() {
        // ...
    }
    
    @objc private func onMainButtonTap() {
        // ...
    }
    
    // MARK: - Public
    func uppercasedInput() -> String? {
        textField.uppercasedInput()
    }
    
    func configure(wit model: ExampleViewControllerDataModel) {
        titleLabel.text = model.title
        
        subtitleLabel.textColor = model.isWarning
        ? Constants.subtitleLabelWarningTextColor
        : Constants.subtitleLabelRegularTextColor
        
        mainButton.setTitle(model.isWarning ? "Back" : "Continue", for: .normal)
        descriptionView.setTitle(model.description)
    }
}

// MARK: - Constants
private enum Constants {
    static let titleFont: UIFont = .boldSystemFont(ofSize: 24)
    static let subtitleLabelFontSize: CFloat = 24.0
    static let subtitleLabelWarningTextColor: UIColor = .red
    static let subtitleLabelRegularTextColor: UIColor = .black
}

// MARK: - UITextFieldDelegate
extension ExampleViewController: UITextFieldDelegate {
    func textFieldDidEndEditing() {
        // ...
    }
}

// MARK: - ExampleOfProtocol
extension ExampleViewController: ExampleOfProtocol {
    func doSomething() {
        // ...
    }
}

// MARK: - UITextField + Extension
private extension UITextField {
    func uppercasedInput() -> String? {
        text?.uppercased()
    }
}

// MARK: - DescriptionView
private class DescriptionView: UIView {
    // ...
    
    func setTitle(_ text: String) {
        // ...
    }
}
```
    
# Використання `// MARK:`

**// MARK:** — це потужний інструмент для структурування та навігації по коду, особливо у великих класах, структурах чи файлах. Його правильне використання допомагає покращити читабельність, полегшує розуміння коду та прискорює роботу з ним.

Використовуйте **// MARK:** для групування властивостей, методів та інших елементів.

## Навіщо використовувати?

1. **Покращення читабельності**: Розділяє логічні блоки коду (наприклад, властивості, методи, ініціалізатори).
2. **Прискорення навігації**: У Xcode розділи, позначені **// MARK:**, відображаються в меню навігації (мапа файлу).
3. **Зменшення когнітивного навантаження**: Структурує файл, полегшуючи роботу з ним.


## Приклади використання
 **1. Структура великого класу**

``` swift
final class ShoppingCartViewController: UIViewController {
    // MARK: - Properties
    private var items: [CartItem] = []

    // MARK: - Init
    init(items: [CartItem]) {
        self.items = items
        super.init(nibName: nil, bundle: nil)
    }

    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }

    // MARK: - Lifecycle
    override func viewDidLoad() {
        super.viewDidLoad()
        setupUI()
    }
    
    // MARK: - Public
    func items() -> [CarItem] {
    	return items
    }

    // MARK: - Private
    private func setupUI() {
        // Do something...
    }

    private func calculateTotal() -> Double {
        return items.reduce(0) { $0 + $1.price }
    }
}
```

## Висновок
* Використовуйте // MARK: для логічного структурування коду.
* Стандартизуйте підхід у команді.
* Дотримуйтесь простоти та читабельності, уникайте надмірної деталізації.

# Використання дужок

У загальному випадку символ "{" не переноситься на новий рядок. Приклади:

* **Умовні операції if, else:**

    ```swift
    if let user = users.first {
        doStuff()
    } else {
        doOtherStuff()
    }
    ```
* **Ланцюг умов:**
 
    Якшо умовний вираз має довгий ланцюг виведення необхідних данних дозволяется перенос "{" на новий рядок

    ```swift
    if let payload = userInfo[Constants.payloadKey] as? [String: Any],
        let action = payload[Constants.actionKey] as? [String: Any],
        let rawType = action[Constants.typeKey] as? String,
        let type = PushNotificationType(rawValue: rawType),
        type == .pushAccessibility
    {
        completionHandler()
        return
    }
    ```

* **Цикли for, while:**

    ```swift
    for item in items {
        item.doStuff()
    }
    ```

* **Визначення класів, протоколів:**

    ```swift
    protocol ServiceDelegate {
        func service(_ service: Service, didFinishLoading error: Error?)
    }
    ```

* **Використання MARK:**

    ```swift
    final class ViewPresenter {
        // MARK: - Private
        private var isShown = false

        // MARK: - Public
        func show() {
            isShown = true
        }
    }
    ```

* **Оператори switch:**

    ```swift
    switch self {
    case .case1: 
        return true
    case .case2: 
        return false
    }
    ```

# Вирази Guard
Під час використання guard-виразів слід дотримуватись загальних правил перенесення рядків:

```swift
func loadData() throws {
    guard !isLoaded else { 
        throw Exception.alreadyLoaded 
    }
}
```

Також дозволяється запис без перенесення, якщо результуючий вираз не є занадто довгим:

```swift
func createViewIfNeeded() {
    guard shouldCreateView else { return }
    // View creation logic
}
```

# Використання if-else

Правильне використання конструкцій **if-else** у Swift допоможе зробити код більш читабельним, підтримуваним та зрозумілим.

## Загальні рекомендації
1. **Ясність і читабельність — головне правило**:
   - Код усередині `if` і `else` має бути легко читабельним і інтуїтивно зрозумілим.
   - Використовуйте зрозумілі умови, уникайте занадто довгих логічних виразів.

2. **Використовуйте `else` тільки за потреби**:
   - Якщо можна уникнути `else`, наприклад, за допомогою раннього виходу (`guard` або `return`), уникайте його.
   - Це покращує читабельність, оскільки зменшує вкладеність коду.

3. **Мінімізуйте вкладеність**:
   - Вкладені конструкції `if`-`else` ускладнюють сприйняття.
   - Краще використовувати ранній вихід (`guard`), щоб запобігти зайвим рівням вкладеності.

4. **Завжди використовуйте фігурні дужки**:
   - Навіть якщо у блоці всього один рядок, додавайте фігурні дужки `{}`. Це знижує ризик помилок під час додавання нових рядків.

## Практика

### **1. Використовуйте `guard` для раннього виходу**

```swift
func process(input: String?) {
    guard let input else {
        print("Input is nil")
        return
    }
    print("Processing \(input)")
}
```
* Такий підхід дозволяє уникнути блоку else і зменшити вкладеність.

### 2. Використовуйте if-else для простої логіки
Якщо логіка складається з кількох умов:

```swift
if value > 0 {
    print("Positive")
} else if value < 0 {
    print("Negative")
} else {
    print("Zero")
}
```

### 3. Використовуйте тернарний оператор для простих умов
Для простих виразів краще використовувати тернарний оператор:

```swift
let result = value > 0 ? "Positive" : "Negative"
```

> **Важливо: Не використовуйте тернарний оператор для складної логіки, щоб уникнути зниження читабельності.**

### 4. Мінімізуйте кількість умов
Якщо є кілька умов, розгляньте використання switch:

```swift
switch value {
case let x where x > 0:
    print("Positive")
case let x where x < 0:
    print("Negative")
default:
    print("Zero")
}
```

### 5. Уникайте логічного негативу
Неправильно ❌:

```swift
if !isValid {
    print("Invalid")
} else {
    print("Valid")
}
```

Правильно ✅:

```swift
if isValid {
    print("Valid")
} else {
    print("Invalid")
}
```

### 6. Занадто довгі умови:

Розбивайте складні умови на окремі змінні або функції.

```swift
let isEligible = age >= 18 && hasPermission && isRegistered
if isEligible {
    print("Eligible")
}
```

### 7. Ігнорування структури:
Якщо блоки if і else занадто довгі, розгляньте рефакторинг у окремі функції.

### 8. Плутанина в логіці:
Переконайтеся, що гілки if і else не перетинаються і охоплюють усі можливі випадки.

### Висновок
* Робіть умови простими та зрозумілими.
* Використовуйте guard для раннього виходу, щоб уникнути вкладеності.
* Дотримуйтесь узгодженого стилю та пишіть код, який буде легко зрозуміти та підтримувати вашій команді.

# Використання .init
У Swift рекомендується уникати використання скорочення .init, якщо можливо, і замість цього використовувати повну назву ініціалізатора. Це робить код більш читабельним і спрощує пошук по проекту.

# Public, Open, Internal
У межах основного таргета модифікатори **open, public, internal** не використовуються (виняток становлять окремі бібліотеки).

# Fileprivate
Модифікатор **fileprivate** застосовується тільки тоді, коли змінна або метод мають використовуватись одним із розширень об'єкта в межах файлу або пов'язаним fileprivate-об'єктом. Важливо чітко розрізняти області видимості **private** та **fileprivate.**

### Приклад:
```swift
final class MainView: UIView {
    private let clildView: ChildView
}

fileprivate final class ChildView: UIView {
    // Some realization
}
```

# Налаштування властивостей View

При використанні **Storyboard** або **XIB**, налаштування властивостей `UIView` (та її підкласів) таких як `backgroundColor`, `cornerRadius`, `shadow`, **виконується виключно з коду**. Це забезпечує більшу контрольованість, прозорість і зручність у підтримці коду.

### **Переваги:**
   - Всі налаштування зосереджені в одному місці.
   - Зміни у налаштуваннях можна легко відстежувати за допомогою системи контролю версій (наприклад, Git).
   - Менше ризику випадково змінити властивості у Storyboard/XIB.
   - Усі зміни стилю і поведінки зберігаються у коді, що зменшує ризик конфліктів з налаштуваннями в Storyboard/XIB.

# Final
Модифікатор final **обов'язково** використовується для об'єктів, які не планується успадковувати (переважна більшість об'єктів).

Для методів, властивостей і сабскриптів, помічених як **final**, компілятор може уникнути використання динамічної диспетчеризації (dynamic dispatch) через таблицю віртуальних функцій (VTable). Натомість використовується статична диспетчеризація, що дозволяє зекономити пам'ять і прискорити доступ.

```swift
final class Service {
}
```

# Make it better

Хорошою практикою э залишати код трохи кращим, ніж він був до вас. Це означає, що, працюючи над функціоналом або виправляючи помилки, варто звертати увагу на загальний стан коду і вносити невеликі покращення там, де це можливо навіть якщо цей код написаний не вами.

### Що це означає на практиці?
   - Видаліть зайві або застарілі частини коду.
   - Розбийте складні функції на менші, зрозумілі методи.
   - Додайте коментарі, якщо код неочевидний.
   - Перевірте, чи відповідає ваш код встановленому кодстайлу команди.
   - Усуньте "дрібні борги", наприклад, неправильне форматування чи дублювання коду.
   - Інше...

### Чому це важливо?

- **Полегшує майбутню підтримку**: Кожен невеликий покращений аспект коду зменшує складність для майбутніх розробників.
- **Формує культуру якості**: Дотримуючись цього принципу, ви подаєте приклад іншим членам команди.

Пам’ятайте: навіть невеликі зміни, такі як виправлення помилки у назві змінної або оновлення застарілого коментаря, роблять ваш код більш якісним і сприяють загальному успіху проєкту.

# Робота з Git

Дотримання єдиного підходу до роботи з Git забезпечує зручність у розробці, спрощує рев’ю коду та підтримку проєкту. Нижче наведено основні правила роботи з Git у нашій команді.

### 1. Іменування гілок
- Використовуйте **kebab-case** у назвах гілок.
- Якщо гілка стосується конкретної задачі, починайте її назву з номера задачі:
> feature/IOS-6021-fix-login-bug
> feature/IOS-6035-add-profile-screen

- Для загальних змін (які не стосуються конкретної задачі) використовуйте описову назву:
> feature/update_readme refactor_network_layer

### 2. Коміти
- Коміти повинні бути змістовними та чіткими.
- Використовуйте англійську мову для опису.
- Уникайте загальних описів на кшталт `fixed bugs`, `updated code`. Натомість пишіть більш конкретно:
  ```
  Fixed incorrect error message on login screen
  Refactored network layer to improve scalability
  ```
- Не приховуйте коміт злиття гілок.
- При злитті гілок залишайте коміт типу `Merge branch 'feature/branch_name' into 'develop'`.
- Це допомагає зберегти прозорість змін і полегшує аналіз історії.

### 3. Історія комітів
- Історія повинна бути якомога лінійнішою.
- Уникайте зайвих розгалужень та хаотичного об’єднання гілок.
- Перед злиттям у основну гілку використовуйте `rebase` для вирівнювання історії (якщо це можливо).
- Для складних змін залишайте чіткі коментарі, щоб пояснити, чому були внесені ті чи інші зміни.

### 4. Правила роботи з Pull Request
- Один Pull Request — одна задача.
- Не змішуйте кілька задач у одному PR.
- Якщо зміни стосуються кількох задач, створюйте окремі гілки та PR для кожної.
- Опис PR має бути чітким та інформативним.
- Вкажіть, яку проблему вирішує PR, що змінюється та як це впливає на функціональність.
- У назву Pull Request спочатку додайте номер таски (якщо вона є) у квадратних дужках: `[IOS-1234] Example of PR name.`
- Проводьте рев’ю коду.
- Усі зміни повинні бути перевірені хоча б одним іншим членом команди.
- Звертайте увагу на відповідність коду до стандартів проєкту, його читабельність та оптимальність.

# Робота з ресурсами

Ефективна організація та використання ресурсів у проєкті є важливою складовою підтримки коду. Нижче наведено основні правила роботи з ресурсами.

### 1. Іменування ресурсів
- Використовуйте **snake_case** для назв файлів ресурсів.
> icon_profile background_main button_add

### 2. Використання зображень
- За можливості, використовуйте векторні зображення.
- Для векторних зображень обов’язково встановлюйте галочку `Preserve Vector Data` в Xcode.
- Використовуйте `Scales: Single scale`.
- Всі однотонні зображення повинні бути у чорному кольорі `#000000`

### 3. Організація ресурсів
- Ресурси повинні бути організовані у відповідних групах та папках у проєкті:
- Уникайте дублікатів ресурсів: однакові зображення або файли не повинні зберігатися під різними іменами.

### 4. Вибір формату
- Завжди віддавайте перевагу векторним зображенням (PDF або SVG), якщо це можливо.
- Растрові зображення (PNG, JPEG) використовуйте лише тоді, коли немає можливості створити векторний файл.

### 5. Приклад налаштування ресурсу
#### Векторне зображення:
- Формат: PDF.
- Налаштування:
- `Render As: Template Image` (для однотонних).
- `Render As: Original Image` (для кольорових).
- Прапорець `Preserve Vector Data`: увімкнено.
- `Scales: Single scale`.

#### Растрове зображення:
- Формат: PNG (або JPEG для фото).
- Налаштування:
- `Render As: Original Image`.
- `Scales: Single scale`.

### 6. Висновок
Дотримання цих правил забезпечує:
- Узгодженість використання ресурсів.
- Полегшену підтримку проєкту.
- Зменшення розміру програми за рахунок оптимізації роботи з ресурсами.
