# Tutorial

Этот **tutorial** написан чтобы **учить и объяснять** разработчикам пошаговое введение в Strapi. ( [Инструкция по началу работы](quick-start.md) является более кратким **How-to** версией .) Этот учебник проведет вас через начальные шаги, по созданию проекта **"FoodAdvisor"** ([Github](https://github.com/strapi/foodadvisor/))([Demo](https://foodadvisor.strapi.io/)).

Вы получите хороший обзор возможностей, которые разработчики любят в Strapi.

<iframe width="800" height="450" src="https://www.youtube.com/embed/vulcVRQ4X8A" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Следуя этому руководству, вы установите и создадите свой первый Strapi проект.

::: tip NOTE

Вам нужно иметь установленные **_Node.js и npm_** в вашей системе, прежде чем следовать этим шагам. Если у вас нет Node.js и npm, пожалуйста, посетите наши [Требования к установке](install-requirements.md).

:::

**Содержание**

[[toc]]

## 1. Установите Strapi и создайте проект

- Перейдите к родительской папке `Projects/` в вашей командной строке.

**Note:** В этом уроке пример предполагает **Projects** папку на вашем **Desktop**. Однако это не обязательно, и вы можете поместить свой проект туда, где вы хотите.

Путь: `~/Desktop/Projects/`

Используем **только одну** из следующих команд, чтобы создать новый проект Strapi:

---

- Для **yarn** чтобы установить Strapi проект (**рекомендуется**). [Установите yarn по этой документации](https://yarnpkg.com/lang/en/docs/install/)

```bash
yarn create strapi-app my-project --quickstart
```

**или**

- Используя **npm/npx** установить проект Strapi

```bash
npx create-strapi-app my-project --quickstart
```

---

Команда создает проект Strapi в папке `my-project/` в вашей родительской папке `Projects/` .

::: tip NOTE

Когда вы создаете новый Quick Start(`--quickstart`) проект, Strapi загружает модули node и необходимые файлы Strapi. С помощью `--quickstart` автоматически выполняет **дополнительные** шаги **построение административной панели** для Strapi и затем **запускает** Strapi. Это открывает браузер и переносит вас на страницу [Welcome](http://localhost:1337/admin/plugins/users-permissions/auth/register).

:::

::: tip NOTE
Вы можете заменить имя `my-project` любым другим по вашему выбору. Например, `yarn create strapi-app my-foodadvisor-project --quickstart` создает папку `./Projects/my-foodadvisor-project`.

:::

Вы видите что-то вроде этого. Вывод ниже показывает, что ваш проект Strapi загружается и устанавливается.

```bash
yarn create v1.17.3
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 🔨  Building fresh packages...
success Installed "create-strapi-app@3.0.0-beta.14" with binaries:
      - create-strapi-app
[#####################################################################] 71/71Creating a new Strapi application at /Users/paulbocuse/Desktop/Projects/my-project.

Creating a quickstart project.
Creating files.
Dependencies installed successfully.

Ваше приложение было создано в /Users/paulbocuse/Desktop/Projects/my-project.

Доступные команды в вашем проекте:

  yarn develop
  Стартует Strapi в режиме наблюдения за изменением кода.

  yarn start
  Стартует Strapi без режима наблюдения за изменением кода.

  yarn build
  Сборка админки Strapi.

  yarn strapi
  Показать все доступные команды.

Вы можете начать командой:

  cd /Users/paulbocuse/Desktop/Projects/my-project
  yarn develop

Запускающей ваше Strapi приложение.

```

Затем, вы заметили следующее, что создает панель администрирования Strapi и автоматически запускается Strapi:

```bash
> my-project@0.1.0 develop /Users/paulbocuse/Desktop/Projects/my-project
> strapi develop

Создание пользовательского интерфейса администратора с настройкой разработки ...

✔ Webpack
  Compiled successfully in 52.21s

[2019-07-30T15:21:17.698Z] info File created: /Users/paulbocuse/Desktop/Projects/my-project/extensions/users-permissions/config/jwt.json
[2019-07-30T15:21:17.701Z] info The server is restarting

[2019-07-30T15:21:19.037Z] info Time: Tue Jul 30 2019 17:21:19 GMT+0200 (Central European Summer Time)
[2019-07-30T15:21:19.037Z] info Launched in: 910 ms
[2019-07-30T15:21:19.038Z] info Environment: development
[2019-07-30T15:21:19.038Z] info Process PID: 70615
[2019-07-30T15:21:19.038Z] info Version: 3.0.0-beta.14 (node v10.16.0)
[2019-07-30T15:21:19.038Z] info To shut down your server, press <CTRL> + C at any time

[2019-07-30T15:21:19.038Z] info ☄️  Admin panel: http://localhost:1337/admin
[2019-07-30T15:21:19.039Z] info ⚡️ Server: http://localhost:1337

```

![Strapi Registration Page](../assets/getting-started/tutorial/strapi-beta-registration-page.png 'Strapi Registration Page')

::: tip NOTE
С помощью `--quickstart` флага устанавливает Страпи, используя [SQLite](https://www.sqlite.org/index.html) БД. Вы можете в любое время оставить **--flag**, но вам нужно выполнить несколько шагов настройки для выбора базы данных. **Перед созданием проекта необходимо, чтобы база данных была установлена ​​и работала локально..**

**Note:**  **SQLite** база данных является отличной базой данных для прототипирования и _developing_ проектов Strapi. **SQLite** это легкая база данных, которая легко переносится на другие реляционные базы данных (**MySQL**, **PostgreSQL**, и **MariaDB**). Рекомендуется **разрабатывать** с SQLite и использовать другую реляционную базу данных (MySQL, PostgreSQL или MariaDB) на production.

**Note:** Если вы хотели бы использовать **MongoDB** на production, вам следует [установить, запустить и использовать MongoDB и для разработки Strapi проекта (в development)](../guides/databases.md#mongodb-installation).
:::

Теперь вы готовы создать новый **Administrator** и нового front-end **User**.

## 2. Создание Administrator и front-end пользователя

Первым шагом является создание **Administrator** (или "root user") для вашего проекта.  **Administrator** имеет все права администратора и права доступа. (Вы можете прочитать больше о том, почему **Administrators** и front-end **Users** являются отдельными [здесь](https://blog.strapi.io/why-we-split-the-management-of-the-admin-users-and-end-users/).)

Вам необходимо заполнить следующие поля:

- **Username**, создать имя пользователя для входа в ваш проект, e.g., `paulbocuse`
- **Password**, создать уникальный пароль для входа в свой проект
- **Email address**, это используется для восстановления
- Отметить **Receive news**, это необязательно, но **рекомендуется**
- Нажмите кнопку **Ready to Start** 

![Завершенная страница регистрации](../assets/getting-started/tutorial/completed-registration-page.png 'Completed Registration Page')

После регистрации **Administrator** , вы увидите Strapi _Administration Dashboard_:

![Strapi Admininstration Dashboard](../assets/getting-started/tutorial/strapi-dashboard.png 'Strapi Admin Dashboard')

**Administrators** и front-end **Users** отдельные роли.

**A.**  **Administrator** имеет доступ и права на Administration Dashboard (или backend) Strapi. **Administrators** может, например, добавить контент, добавить плагины и загрузить изображения.

**B.** front-end **User** это тот, кто взаимодействует с вашим проектом через front-end. Front-end **User** может, например, стать «Автором» статьи, совершить покупку, иметь аккаунт, оставить отзыв или оставить комментарий.

До этого момента вы создали **Administrator**, и поэтому вы хотите создать интерфейс **User**.

**Note:** Нет необходимости всегда создавать интерфейс **User** для **Administrators**; в этом случае **Administrator** также front-end **User** как «Автор» контента в приложении.

- Кликните `Users`  под **CONTENT TYPES** в левом меню
- Кликните голубую кнопку **+ Add New User** в правом верхнем углу
- Заполните поля `Username`, `Email`, и `Password`
- Выделите `ON` для **Подтверждения** полей переключения
- Справа под **Role**, выделите `Authenticated`
- Сохранить нового пользователя, нажав синиюю кнопку **Save** (вверху справа)

![новый фронт-энд User](../assets/getting-started/tutorial/new-front-end-user.png 'New front-end User')

Теперь вы готовы создать свой первый **Content Type**.

## 3. Создание нового Content Type с именем "Restaurant"

**Content Types** представляют собой набор введенных данных, представленных полями. Например **Content Type**  `Restaurant` может быть предназначен для отображения информации о ресторанах. `restaurant` **Content Type** может иметь поля, которые включают в себя `name`, главное `image`, и `description` - _это минимум_. Тем не менее,`restaurant` также может иметь `category` или несколько `categories`, и `restaurant` может быть, нужно показать `hoursofoperation`.

**Content Type** можно считать своего рода _blueprint_ для созданных данных. Другими словами, **Content Type** это схема структуры данных.

В следующем разделе описываются шаги, необходимые для каждого из них выше. **Content Type** поля.

::: tip NOTE

Дополнительные **Ресторан** тематические **Content Type** и поля можно увидеть в [FoodAdvisor demo site](https://foodadvisor.strapi.io/).

:::

### Restaurant Content Type

- Перейдите к плагину **Content Type Builder**, находится в левом меню: в **PLUGINS**: --> **Content Type Builder**

Теперь вы можете увидеть три доступных **Content Types**. На данный момент доступны три Content Types `Permission`, `Role`, и `Users`.

![Content Type Dashboard](../assets/getting-started/tutorial/content-type-dashboard.png 'Content Type Dashboard')

Вам нужно создать новый **Content Type** для `Restaurants`.

1. Выполните эти шаги, чтобы **добавить Restaurant Content Type**:

- Кликните ссылку `+ Add A Content Type` (под имеющимся **CONTENT TYPES**)
- Введите **Name** для вашего нового **Content Type** (вызовите этот `restaurant`), и вы сможете написать `Restaurant Listings` для **Description**
- Кликните кнопку `Done`

![Записи единственного имени для типа контента](../assets/getting-started/tutorial/singular-name-entry.png 'Singular Name Entries или Content Type')

::: tip NOTE

Тип контента **Name** всегда **единственное число**. Например, `restaurant` не `restaurants`.

:::

1. Вы сейчас на панели **Field Selection** :

Вы можете добавить свое первое поле, **String** для имени **Restaurant**.

![Field Section Panel](../assets/getting-started/tutorial/field-selection-panel.png 'Field Selection Panel')

- Нажмите поле `String` 
- В поле **Name**, типа `name`

![Restaurant Name Input Field](../assets/getting-started/tutorial/restaurant-name-input-field.png 'Restuarant Name Input Field')

- Кликните по вкладке `ADVANCED SETTINGS`
- Отметьте `Required field` checkbox
- Отметьте `Unique field` checkbox

![Restaurant Name Advanced Settings](../assets/getting-started/tutorial/restaurant-name-advanced-settings.png 'Restuarant Name Advanced Settings')

- Нажмите кнопку `+ Add Another Field` 

Теперь вы готовы добавить второе поле, поле **Rich Text** для описания **Restaurant**.

![Field Section Panel](../assets/getting-started/tutorial/field-selection-panel.png 'Field Selection Panel')

- Нажмите поле `Rich Text` 

- В поле **Name** , введите `description`

![Restaurant Rich Text Field](../assets/getting-started/tutorial/restaurant-rich-text-field.png 'Restuarant Rich Text Field')

- Нажмите кнопку `+ Add Another Field`

Теперь вы готовы добавить третье поле, поле **Media** для маленького изображения **Restaurant**.

![Field Section Panel](../assets/getting-started/tutorial/field-selection-panel.png 'Field Selection Panel')

- Кликните поле `Media`

- В поле **Name**, введите `image`

![Restaurant Rich Image Field](../assets/getting-started/tutorial/restaurant-image-field.png 'Restuarant Rich Image Field')

- Нажмите на вкладку **ADVANCED SETTINGS**
- Отметьте `Required field` checkbox

![Restaurant Rich Image Field Advanced Settings](../assets/getting-started/tutorial/restaurant-image-field-advanced-settings.png 'Restuarant Rich Image Field Advanced Settings')

- Нажмите на `Done` кнопку

Ваш новый Content Type называющийся **Restaurant** готов к **Saved**.

![Restaurant Save Screen](../assets/getting-started/tutorial/restaurant-save-screen.png 'Restuarant Save Screen')

- Нажмите на `Save` button

- Подождите пока Strapi перезапуститься

![Strapi Restart](../assets/getting-started/tutorial/strapi-restart.png 'Strapi Restart')

После перезапуска Strapi, вы готовы продолжать создавать `Category` **Content Type**.

## 4. Создание нового Content Type называемого "Category"

### Category Content Type

 `Category` **Content Type** будет иметь **String** поле с именем `category`, и **Relation field** с отношением **Многие ко многим** .

![Category Add Content Type](../assets/getting-started/tutorial/category-add-content-type.png 'Category Add Content Type')

1. Выполните эти шаги, чтобы **добавить Category Content Type**:

- Нажмите на ссылку `+ Add A Content Type` 
- Введите **Name** для вашего нового **Content Type** (назовите его `category`)
- Введите `Restaurant Categories` для **Description**

![Category Name Field](../assets/getting-started/tutorial/category-name-field.png 'Category Name Field')

- Нажмите на кнопку `Done`

1. Теперь вы готовы добавить поля к вашему **Category**:

![Category Fields](../assets/getting-started/tutorial/category-fields.png 'Category Fields')

- Нажмите поле `String`
- В поле **Name**, введите `name`

![Category Name Entry Field](../assets/getting-started/tutorial/category-name-entry-field.png 'Category Name Entry Fields')

- Нажмите вкладку `ADVANCED SETTINGS`
- Отметьте чекбокс `Required field`
- Отметьте чекбокс `Unique field`

![Category Advanced Settings](../assets/getting-started/tutorial/category-advanced-settings.png 'Category Advanced Settings')

- Нажмите на кнопку `+ Add Another Field`

Теперь вы готовы добавить второе поле, поле **Relation** для создания отношения **Многое ко многим** отношения между Content Types **Category** и **Restaurant**.

- Нажми на поле `Relation`

![Category Add Field Panel](../assets/getting-started/tutorial/category-add-field-panel.png 'Category Add Field Panel')

Это приводит вас к экрану **Add New Relation**.

![Category New Relation Field](../assets/getting-started/tutorial/category-new-relation-field.png 'Category New Relation Field')

- нажмите на _right dropdown_ с `Permission (Users-Permissions)` и измените его на `Restaurant`

![Category Relation Dropdown](../assets/getting-started/tutorial/category-relation-dropdown.png 'Category Relation Dropdown')

- Нажмите на иконку `Many to Many` (от выбора средней иконки). Это читается как, **"Категории есть и принадлежит многим ресторанам"**

![Category Relation Many to Many](../assets/getting-started/tutorial/category-relation-many-to-many.png 'Category Relation Many to Many')

- Нажмите на кнопку `Done`

![Category Save](../assets/getting-started/tutorial/category-save.png 'Category Save')

- Нажмите на кнопку `Save`

- Подождите, пока Strapi перезапустится

![Category Save Strapi Restart](../assets/getting-started/tutorial/category-save-strapi-restart.png 'Category Save Strapi Restart')

После перезапуска Strapi вы готовы создать `Группа и повторяемое поле` (Группа и повторяемое поле)  **"Hours of Operations."** (Часы работы)

## 5. Создание новой Group, and Repeatable Field - "Hours of Operation"

### Группа Hours of Operation

`Restaurant` Content Type имеет поле **Group** с именем `Hours_of_operation`. Эта группа **Repeatable** (повторяемая) и для отображения **Opening hours** и **Closing hours** у **Restaurant**.

1. Выполните эти шаги, чтобы **добавить новую группу**:

- Нажмите на ссылку `+ Add A Group` чтобы добавить новую группу **Group**
- Введите **Name** для вашего нового **Group** (называемого `hours_of_operation`), и вы можете написать `Hours of Operation` для **Description**

![Hours of Operation Add Group](../assets/getting-started/tutorial/hours-of-operation-add-group.png 'Hours of Operation Add Group')

- Нажмите на кнопку `Done` 

2. Теперь вы готовы добавить поля к вашему **Group**:

![Hours of Operation Add Fields](../assets/getting-started/tutorial/hours-of-operation-add-fields.png 'Hours of Operation Add Fields')

- Нажмите на поле `String`
- В поле **Name** , введите `day_interval`. Это чтобы ввести **Day (or Days)** с **Hours of Operation**

![Hours of Operation Days](../assets/getting-started/tutorial/hours-of-operation-days.png 'Hours of Operation Days')

- Нажмите вкладку `ADVANCED SETTINGS`
- Проверьте чкбокс `Required field` 

![Hours of Operation Days Advanced Settings](../assets/getting-started/tutorial/hours-of-operation-days-advanced-settings.png 'Hours of Operation Days Advanced Settings')

- Нажмите на `+ Add Another Field`

Теперь вы готовы добавить второе поле, другое поле **String** для **Opening Hours**.

![Hours of Operation Opening Hours](../assets/getting-started/tutorial/hours-of-operation-opening-hours.png 'Hours of Operation Opening Hours')

- Нажмите на поле `String` 
- В поле **Name** , введите `opening_hours`

![Hours of Operation Opening Hours Name](../assets/getting-started/tutorial/hours-of-operation-opening-hours-name.png 'Hours of Operation Opening Hours Name')

- Нажмите на кнопку `+ Add Another Field` 

Теперь вы готовы добавить третье поле, еще одно поле **String** для **Closing Hours**.

![Hours of Operation Closing Hours](../assets/getting-started/tutorial/hours-of-operation-closing-hours.png 'Hours of Operation Closing Hours')

- Нажмите на поле `String`
- В поле **name** введите `closing_hours`

![Hours of Operation Closing Hours Name](../assets/getting-started/tutorial/hours-of-operation-closing-hours-name.png 'Hours of Operation Closing Hours Name')

- Нажмите на кнопку `Done`

![Hours of Operation Save](../assets/getting-started/tutorial/hours-of-operation-save.png 'Hours of Operation Save')

- Нажмите на кнопку `Save` 
- Подождите, пока Strapi перезапустится

![Hours of Operation Strapi Restart](../assets/getting-started/tutorial/hours-of-operation-strapi-restart.png 'Hours of Operation Strapi Restart')

После перезапуска Strapi вы готовы назначить эту группу **Hours_of_operation** на **Restaurant** Content Type.

**Note:** Можно было бы назначить группу **Hours_of_operation** другому **Content Type**, скажем, **Cafe** Content Type. У вас есть возможность повторно использовать эту группу в вашем приложении.

1. Далее вам нужно назначить **Hours_of_operation** Group на **Restaurant** Content Type.

Чтобы получить доступ к **Hours_of_operation** Group изнутри **Restaurant** Content Type, вам надо **edit**  **Restaurant** Content Type в **Content Type Builder**.

- При необходимости вернитесь к **Content Type Builder**

![Edit Restaurant Content Type](../assets/getting-started/tutorial/edit-restaurant-content-type.png 'Edit Restaurant Content Type')

- НАжмите на `Restaurant` Content Type, в **CONTENT TYPES**

![Edit Restaurant Add Another Field](../assets/getting-started/tutorial/edit-restaurant-add-another-field.png 'Edit Restaurant Add Another Field')

- Нажмите на кнопку `+ Add Another Field` , чтобы добавить **Group**

![Edit Restaurant Group Field](../assets/getting-started/tutorial/edit-restaurant-group-field.png 'Edit Restaurant Group Field')

- Нажмите поле `Group` 

- обеспечьте `hours_of_operation` is displayed в выпадающем **Select a group**
- Предоставьте **name** для этой группы в **Restaurant** Content Type. E.g., `restaurant_hours`
- Отметьте `Repeatable field` 

![Restaurant Group Inputs](../assets/getting-started/tutorial/restaurant-group-inputs.png 'Restaurant Group Inputs')

- Нажми на вкладку `ADVANCED SETTINGS`
- Отметьте `Required field`

![Restaurant Group Advanced Settings](../assets/getting-started/tutorial/restaurant-group-advanced-settings.png 'Restaurant Group Advanced Settings')

- Нажмите на `Done` button

![Restaurant Group Save](../assets/getting-started/tutorial/restaurant-group-save.png 'Restaurant Group save')

- Нажмите на `Save` button

- Подождите, пока Strapi перезапустится

![Restaurant Group Strapi Restart](../assets/getting-started/tutorial/restaurant-group-strapi-restart.png 'Restaurant Group Strapi Restart')

После рестарта Strapi, Вы готовы перейти к следующему разделу где вы настраиваете пользовательский интерфейс вашего **Restaurant** Content Type.

1. Далее вы редактируете **View Settings** для нового **Hoursofoperation Group** изнутри **Content Manager**.

Вы можете _drag and drop_ поля в different layout, также как и, _rename the labels_ в качестве двух примеров того, как вы можете настроить пользовательский интерфейс для вашего **Content Types**.

- Перейдите к и нажмите на `Content Manager`, в **PLUGINS** в меню слева

![Content Manager](../assets/getting-started/tutorial/content-manager.png 'Content Manager')

- Нажмите на вкладку `Groups(1)`

![Content Manager Groups Tab](../assets/getting-started/tutorial/content-manager-groups-tab.png 'Content Manager Groups Tab')

- Нажмите на `Hours_of_operation` для изменения **View Settings**

![Content Manager Hoursofoperation](../assets/getting-started/tutorial/content-manager-hoursofoperation.png 'Content Manager Hoursofoperation')

- Переставьте поля и сделайте их более удобными для пользователя. Зажмите `opening_hours` и сдвиньте его рядом с`closing_hours`

![Content Manager Hoursofoperation Rearrange Fields](../assets/getting-started/tutorial/content-manager-hoursofoperation-rearrange-fields.png 'Content Manager Hoursofoperation Rearrange Fields')

Далее вы измените **field labels** чтобы их было легче понять:

- Нажми на поле `day_interval`
- Измените **Label** читать, `Day (or Days)`
- Добавьте **Description**, `Вы можете ввести один день или серию дней, чтобы заполнить это поле. E.g. "Tuesday" или "Tues - Wed"`

![Content Manager Hoursofoperation Day Interval](../assets/getting-started/tutorial/content-manager-hoursofoperation-day-interval.png 'Content Manager Hoursofoperation Day Interval')

- Нажми на поле `opening_hours` 
- Измените **Label** to read, `Opening Hours`

![Content Manager Hoursofoperation Opening Hours](../assets/getting-started/tutorial/content-manager-hoursofoperation-day-opening-hours.png 'Content Manager Hoursofoperation Day Opening Hours')

- Нажмите поле `closing_hours`
- Измените **Label** to read, `Closing Hours`

![Content Manager Hoursofoperation Closing Hours](../assets/getting-started/tutorial/content-manager-hoursofoperation-day-closing-hours.png 'Content Manager Hoursofoperation Day Closing Hours')

- Нажмите на кнопку `Save`, и затем кнопку `Confirm` сохранить ваши настройки

Ваши настройки теперь сохранены.

Всякий раз, когда кто-то вводит информацию для **Restaurant**, форма заявки понятна. С помощью Strapi вы можете изменить эти и другие параметры, чтобы обеспечить наилучшее впечатление.

Вы готовы начать вводить фактический контент.

## 6. Управление и добавление контента в "Restaurant" Content Type

Теперь вы готовы добавить некоторые **Restaurants** и **Categories**.

1. Вы сейчас собираетесь ввести новый **Restaurant**

- Перейдите к и нажмите на `Restaurants`, в **CONTENT TYPES** в левом меню

![Restaurants Content Type](../assets/getting-started/tutorial/restaurants-content-type.png 'Restaurants Content Type')

- Далее нажмите на кнопку **+ Add new Restaurant** (в правом верхнем углу)
- Введите следующую информацию для вашего первого **Restaurant** под названием **Biscotte Restaurant**
  - В поле **Name** , введите `Biscotte Restaurant`
  - В поле **Description** , введите `Добро пожаловать в Biscotte ресторан! Ресторан Biscotte предлагает кухню, основанную на свежих, качественных продуктах, часто местных, органических, когда это возможно, и всегда производимых страстными производителями.`
  - Загрузить **Image** представляющий **Restaurant**

**Note:** На этом этапе вы обычно выбираете **Categories** для этого **Restaurant**. Вы не ввели ни одного **Categories**, так что вы делаете этот шаг после ввода этого первого **Restaurant**.

![Restaurant Content Type Basic Data](../assets/getting-started/tutorial/restaurant-content-type-basic-data.png 'Restaurant Content Type Basic Data')

- Далее прокрутите вниз до **RestaurantHours|(0)** и нажмите на кнопку `+ ADD NEW ENTRY`
  - В секции **Create an Entry** , введите следующие данные:
    - В поле **Days (or Days)**, введите `Sun - Mon`
    - В поле **Opening Hours**, введите `Closed`
    - **Skip** поле **Closing Hours** , как это **Restaurant** закрыт весь день
  - Нажмите на кнопку `+ ADD NEW ENTRY` создать еще одну новую запись
    - В поле **Days (or Days)** , введите `Tues - Fri`
    - В поле **Opening Hours** , введите `12:00`
    - В поле **Closing Hours** , введите `22:30`
  - Нажмите на кнопку `+ ADD NEW ENTRY` создать последнюю запись
    - В поле **Days (or Days)** введите `Sat`
    - В поле **Opening Hours** введите `11:30`
    - В поле **Closing Hours** введите `16:00`

Теперь вы ввели всю необходимую информацию, для вашего первого **Restaurant**.

![Restaurants Entry](../assets/getting-started/tutorial/restaurants-entry.png 'Restaurants Entry')

- **Scroll up** и нажмите на кнопку `Save` 

Далее нужно войти в некоторые **Categories** что может относиться к вышесказанному и другим **Restaurants**.

- Перейдите к и нажмите на `Categories`, в **CONTENT TYPES** В left-hand меню

![Categories Entry](../assets/getting-started/tutorial/categories-content-type.png 'Categories Entry')

Вы собираетесь ввести два **Categories**, но вы могли бы добавить так много **Categories** как вам нужно. Позже вы можете добавить дополнительные **Categories** и назначить их существующим и новым **Restaurants**.

- Нажмите кнопку `+ Add New Category`
  - В поле **Name** , введите `French food`
  - В выпадающем **Restaurants(0)** , выделите `Biscotte Restaurant`

![Categories Entry 1](../assets/getting-started/tutorial/categories-entry-1.png 'Categories Entry 1')

- Нажмите на кнопку `Save`

Теперь вы вводите свой второй **Category**.

- Нажмите на кнопку `+ Add New Category`
  - В поле **Name**, введите `Brunch`
  - В поле **Restaurants(0)** dropdown, выделите `Biscotte Restaurant`

![Categories Entry 2](../assets/getting-started/tutorial/categories-entry-2.png 'Categories Entry 2')

- Нажмите на  кнопку `Save`

Вы ввели свой первый **Restaurant** Content Type. Вы также назначили два **Categories** к этому **Restaurant**. Ваш следующий шаг - установить **Roles and Permissions**.

## 7. Установить роли и разрешения

По умолчанию, Strapi публикует все **Content Types** с ограниченными разрешениями. Это означает, что вы должны явно дать разрешения каждому созданному вами **Content Type**. Вы собираетесь дать **Public** API (или URL) доступ к обоим **Restaurant** Content Type и **Category** Content Type.

- Нажми на `Roles & Permissions` menu item, в **PLUGINS** В left-hand-menu
- Перейдите и нажмите на **Roles & Permissions** пункт меню под **PLUGINS** в левом меню

![Roles and Permissions](../assets/getting-started/tutorial/roles-and-permissions.png 'Roles And Permissions')

- Next, нажми на **Public** Role

![Roles and Permissions Public Role](../assets/getting-started/tutorial/roles-and-permissions-public-role.png 'Roles And Permissions Public Role')

- Далее прокрутите вниз под **Permissions** и locate the **Restaurant** и **Category** Content Types
- Нажмите на checkbox для **find** и **findone** В **Restaurant** Content Type
- Нажмите на checkbox для **find** и **findone** В **Category** Content Type

![Roles and Permissions Find Permissions](../assets/getting-started/tutorial/roles-and-permissions-find-permissions.png 'Roles And Permissions Find Permissions')

- Вернитесь к началу и нажмите на **Save** button

![Roles and Permissions Save](../assets/getting-started/tutorial/roles-and-permissions-save.png 'Roles And Permissions Save')

Вы теперь открыли API и готовы потреблять ваш контент.

## 8. Потребление Content Type API

Каждый из ваших **Content Types** доступны по их автоматически сгенерированным маршрутам.

Оба ваши **Restaurant** и **Category** Content Types теперь можно получить доступ:

- В вашем браузере, перейдите `http://localhost:1337/restaurants` чтобы получить данные для разрешенного **Find** value of your **Restaurant** Content Type

![Restaurant Api](../assets/getting-started/tutorial/restaurant-api.png 'Restaurant API')

- В вашем браузере, перейдите `http://localhost:1337/categories` вернуть данные для разрешенного **Find** value of your **Category** Content Type

![Category Api](../assets/getting-started/tutorial/category-api.png 'Category API')

::: tip NOTE

Если вы неправильно установили разрешения для своего типа контента, вы получите **"403"** ошибка разрешения. Смотрите пример ниже.

Запрещенный доступ выглядит так:

![Forbidden Access to Restaurant Content Type](../assets/getting-started/tutorial/permission-forbidden-access.png 'Forbidden Access to Restaurant Content Type')
:::

::: tip NOTE

Если вы хотите увидеть маршрут какого-либо конкретного **Content Type**, вам нужно перейти к **Content Type** в плагин **Roles and Permissions** и нажмите на ⚙️ next to the value. Справа вы видите маршрут:

![Permission Routes](../assets/getting-started/tutorial/permission-routes.png 'Permission Routes')

:::

::: tip CONGRATULATIONS
👏 Поздравляем, вы завершили **Strapi Getting Started Tutorial**. Куда пойти дальше?

- Узнайте, как использовать Strapi с React ([Gatsby](https://blog.strapi.io/building-a-static-website-using-gatsby-and-strapi) или [Next.js](https://blog.strapi.io/strapi-next-setup/)) или Vue.js ([Nuxt.js](https://blog.strapi.io/cooking-a-deliveroo-clone-with-nuxt-vue-js-graphql-strapi-and-stripe-setup-part-1-7/)).
- Прочтите **concepts** чтобы погрузиться в Strapi
- Получить помощь по [StackOverflow](https://stackoverflow.com/questions/tagged/strapi)
- Прочитайте [source code](https://github.com/strapi/strapi), [contribute](https://github.com/strapi/strapi/blob/master/CONTRIBUTING.md) и [give a star](https://github.com/strapi/strapi) в GitHub
- перейдитеs в [Twitter](https://twitter.com/strapijs) получать последние новости
- [JoВ vibrant and active Strapi community](https://slack.strapi.io) в Slack
  :::
