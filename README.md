## task1

### 1. Переносим отдельный коммит в main
Переключаемся на основную ветку `main` и помещаем в нее нужный коммит из ветки `feature2` командами

```bash
git checkout main
git cherry-pick feature2
````
<img width="1277" height="217" alt="image" src="https://github.com/user-attachments/assets/887a62d2-bf97-4d2c-b96e-5c671da2455d" />

---

### 2. Создаем `feature3`

Создаем `feature3` от текущего состояния `main`

```
git branch feature3
```
<img width="1173" height="67" alt="image" src="https://github.com/user-attachments/assets/8d3286b9-a47f-4dcd-8e5a-292d7d17963a" />

---

### 3. Перебазирование и слияние `feature1`

Переносим коммиты из ветки `feature1` поверх  `main` , потом выполняем merge


```
git checkout feature1
git rebase main
git checkout main
git merge feature1
```
<img width="1153" height="842" alt="image" src="https://github.com/user-attachments/assets/49124dd9-bbb0-43a1-ba74-4d0cf7913228" />

---

### 4. Склеиваем коммиты

Объединяем два последних перенесенных коммита ветки `main` в один перебазированием. В открывшемся редакторе меняем `pick` на `squash` для второго коммита и сохраняем новое описание task1+task2

```
git rebase -i HEAD~2
```
<img width="1244" height="391" alt="image" src="https://github.com/user-attachments/assets/0c430c3f-c96d-4f20-8340-4411536d4b29" />

---

### 5. Создаем file6 в `feature3`

Переходим в  `feature3`, добавляем новый файл `file6` и фиксируем изменения

```
git checkout feature3
touch file6
git add file6
git commit -m "Add file6 to feature3"
```
<img width="1237" height="108" alt="image" src="https://github.com/user-attachments/assets/fb680949-b20c-4f98-aecb-728af814db4a" />
<img width="1521" height="183" alt="image" src="https://github.com/user-attachments/assets/79aa28e2-889a-4503-a03e-d354510ded2b" />

---

### 6. Удаляем ненужные ветки

Удаляем ветки `feature1` и `feature2`, так как они нам больше не нужны

```
git branch -D feature1
git branch -D feature2
```
<img width="1247" height="176" alt="image" src="https://github.com/user-attachments/assets/dbc4023e-c260-4c3a-9e99-e58e1f61cd5d" />

---

### 7. Пушим на гитхаб

Так как история коммитов была переписана, принудительно обновляем `main`, пушим новую ветку и удаляем неактуальные ветки

```
git checkout main
git push -f origin main

git checkout feature3
git push -u origin feature3

git push origin --delete feature1
git push origin --delete feature2
```
<img width="1365" height="993" alt="image" src="https://github.com/user-attachments/assets/3c287375-0ba3-46f6-bd56-d8ea34583c05" />
<img width="1585" height="339" alt="image" src="https://github.com/user-attachments/assets/acb11e57-cebb-41df-a1bf-96c17a603659" />
