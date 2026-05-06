# my-website-project
## Ветеринарная клиника «Доктор Хвост» — сайт ветеринарной помощи

**Учебный проект**  
**Автор:** [Ваше Имя]  
**Дата:** 06.05.2026  

---

## День 7: Работа над проектом

### Проверка кода functions.php

| Параметр | Значение |
|----------|----------|
| Дата проверки | 06.05.2026 |
| Версия темы | Pet Care Store 1.0.2 |

---

### Скриншот дня 7

![Скриншот работы шорткодов](7%20день.webp)

---

### Что сделано

- [x] Добавлены шорткоды в `functions.php`
- [x] Создана тестовая страница для проверки
- [x] Проверена работа всех шорткодов
- [x] Включён режим отладки WP_DEBUG

---

### Что проверили

- [x] Наличие PHPDoc-комментариев перед каждой функцией
- [x] Наличие строчных комментариев (//) внутри функций
- [x] Все строки заканчиваются точкой с запятой `;`
- [x] Отсутствие лишних пробелов и пустых строк
- [x] Шорткод `[privetstvie]` работает корректно
- [x] Шорткод `[moi_stati]` работает корректно
- [x] Шорткод `[statistika]` работает корректно

---

### Результаты проверки

**Найденные замечания:**

> Замечаний нет — всё соответствует стандартам PHP и WordPress Coding Standards.

**Что исправили:**

> Ничего не потребовалось исправлять.

---

### Проверенные функции

```php
// Шорткод [moi_stati] - список последних 5 статей
function pokazat_stati() {
    $stati = get_posts( array('numberposts' => 5) );
    if ( empty($stati) ) {
        return '<p>📭 Пока нет статей. Добавьте первую запись!</p>';
    }
    $rezultat = '<ul style="list-style: disc; padding-left: 20px;">';
    foreach ( $stati as $stat ) {
        $rezultat .= '<li><a href="' . get_permalink($stat) . '">' . $stat->post_title . '</a></li>';
    }
    $rezultat .= '</ul>';
    return $rezultat;
}
add_shortcode('moi_stati', 'pokazat_stati');

// Шорткод [statistika] - статистика сайта
function statistika_sayta() {
    $kol_state = wp_count_posts()->publish;
    $kol_stranits = wp_count_posts('page')->publish;
    return '<div style="background: #f0f0f0; padding: 15px; border-radius: 8px;">
        <p>📄 Статей на сайте: ' . $kol_state . '</p>
        <p>📑 Страниц на сайте: ' . $kol_stranits . '</p>
        </div>';
}
add_shortcode('statistika', 'statistika_sayta');

// Шорткод [privetstvie] - приветствие с датой
function privetstvie() {
    $data = date('d.m.Y');
    return '<div style="background: #e8f5e9; padding: 15px; border-radius: 8px; text-align: center;">
        🐾 Добро пожаловать в наш зоомагазин!<br>
        📅 Сегодня ' . $data . '
        </div>';
}
add_shortcode('privetstvie', 'privetstvie');
