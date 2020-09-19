# digital-superhero-hack
Разработка сервиса по определению мест концентрации ДТП

# Задача
Необходимо создать удобный web-сервис для определения мест концентрации дорожно-транспортных происшествий (далее – ДТП) в соответствии с действующим законодательством и выработки рекомендаций по оптимальному размещению комплексов фото- видеофиксации (далее – ФВФ).

# Методика оценки эффективности размещения комплексов ФВФ
## Методология тройной разности
Оригинальный материал доступен по [ссылке](https://habr.com/ru/company/ods/blog/416101/), [видео](https://www.youtube.com/watch?v=XWw4Wi6K0QU).

![МТР](https://habrastorage.org/webt/ba/td/_5/batd_5frmr2br4ewpfm18yitl-c.png)

Под пилотом будем понимать эксперимент с размещением комплексов ФВФ.
Для оценки эффективности на первом этапе следует выбрать 2 участка дорог (перекрестка, поворота, населенных пункта и тд): один для контрольной группы (зеленый) и один для тестовой группы (синий).
Введем следующие обозначения:

- ![formula](https://render.githubusercontent.com/render/math?math=t_2): дата начала пилота;

- ![formula](https://render.githubusercontent.com/render/math?math=t_3): дата окончания пилота;

- ![formula](https://render.githubusercontent.com/render/math?math=t_0=t_2-oneyear): дата, соответствующая дате начала пилота в прошлом году;

- ![formula](https://render.githubusercontent.com/render/math?math=t_1=t_3-oneyear): дата, соответствующая дате окончания пилота в прошлом году.

Таким образом, у нас есть два периода времени:

- ![formula](https://render.githubusercontent.com/render/math?math=[t_2,t_3]): период пилота;

- ![formula](https://render.githubusercontent.com/render/math?math=[t_0,t_1]): период, соответствующий периоду пилота в прошлом году.

Предлагается сравнить количество ДТП тестового участка дороги и контрольного на периодах пилота и год назад. Для этого нужно посчитать три группы разностей. Обозначим количество ДТП в день t на тестовом участке дороги за ![formula](https://render.githubusercontent.com/render/math?math=x_t^T), а ![formula](https://render.githubusercontent.com/render/math?math=x_t^C) — на контрольном. Группа первая задает базисную линию от которой будет измеряться рост или падение количества ДТП в пилотный период:

- ![formula](https://render.githubusercontent.com/render/math?math=\delta^T_1=x^T_{t_2}-x^T_{t_0}): разница в количестве ДТП между началом пилота и той же датой год назад на тестовом участке дороги;

- ![formula](https://render.githubusercontent.com/render/math?math=\delta^T_2=x^T_{t_3}-x^T_{t_1}): разница в количестве ДТП между окончанием пилота и той же датой год назад на тестовом участке дороги;

- ![formula](https://render.githubusercontent.com/render/math?math=\delta^C_1=x^C_{t_2}-x^C_{t_0}): разница в количестве ДТП между началом пилота и той же датой год назад на контрольном участке дороги;

- ![formula](https://render.githubusercontent.com/render/math?math=\delta^C_2=x^C_{t_3}-x^C_{t_1}): разница в количестве ДТП между окончанием пилота и той же датой год назад на контрольном участке дороги;

Вторая группа разностей, задает рост или падение количества ДТП в пилотный период:

- ![formula](https://render.githubusercontent.com/render/math?math=\delta^T=\delta^T_2-\delta^T_1): разница в количестве ДТП между окончанием пилота и началом пилота на тестовом участке дороги (скорректированная относительно дат год назад);

- ![formula](https://render.githubusercontent.com/render/math?math=\delta^C=\delta^C_2-\delta^C_1): разница в количестве ДТП между окончанием пилота и началом пилота на контрольном участке дороги (скорректированная относительно дат год назад);

Решающая разность определяет где удалось достичь большего снижения количества ДТП в пилотный период:
- ![formula](https://render.githubusercontent.com/render/math?math=\delta=\delta^T-\delta^C)

Если ![formula](https://render.githubusercontent.com/render/math?math=\delta>0), значит размещение комплексов ФВФ дает положительный эффект (сокращение количества ДТП).
