≡ Краткое руководство

# Введение в контроль версий.
### Краткая инструкция по работе с git
***
1. Установка Git - скачать [git](https://git-scm.com/downloads) 
2. Создать файл с расширением `.md` - лучше выделить отдельную папку в которой будет лежать данный файл.
3. Открыть IDE в которой будете работать.
4. Далее нужно создать git репозиторий из этого каталога, выполните команду `git init`.  
>Response:  
   $ git init
    Initialized empty Git repository in     /Users/git/***/.git/

5. Далее нужно познакомить git с нами, для этого нужно обозначить себя назвав свое имя и email 
> первая команда: `git config --global user.name "Вашк имя"`
> вторая команда: `git config --global user.email "Ваш емейл"`

Теперь мы познакимили гит с нами и в каждом нашем коммите будет фигурировать наше имя и емейл для возможности связаться с нами другим участникам разработки.

6. Чтоб сохранить изменение в файле .md нужно выоплнить команду `git add "название файла.md` и `git commit -m "some text"`.  
>  Response:  
 [master 12cc696] some text
 1 file changed, 1 insertion(+)
 
7. Используйте команду `git status`, чтобы проверить текущее состояние репозитория.
>  Response:  
On branch master  
nothing to commit, working tree clean

Команда проверки состояния сообщит, что коммитить нечего. Это означает, что в репозитории хранится текущее состояние рабочего каталога, и нет никаких изменений, ожидающих записи.

8. Если внести изменение в файл и сохранить их, но не вызывать команду `git add "filename.md`, то команда `git status` вернет:
>  Response:  
>  On branch master  
Changes not staged for commit:  
  (use "git add <file>..." to update what will be committed)  
  (use "git restore <file>..." to discard changes in working directory)  
        modified:   filename.md  
no changes added to commit (use "git add" and/or "git commit -a")

Это значит что:  
> git знает, что файл .md был изменен, но при этом эти изменения еще не зафиксированы в репозитории.

> Также сообщение о состоянии дает вам подсказку о том, что нужно делать дальше. Если вы хотите добавить эти изменения в репозиторий, используйте команду git add. В противном случае используйте команду git сheckout для отмены изменений.

9. Для создания ветки используем команду  `git branch <название ветки>`
10. Для отображения всех веток которые есть на локальной машине используе команду `git branch` - в ответе будет подсвечено в какой именно ветке находится пользователь:
>  Response:
>* master  
  название ветки №2
11. Для переключение между ветками используем команду `git checkout <название ветки>`.
>  Response:  
>Switched to branch 'название ветки'
12. Для того чтобы смержить изменения нужно выполнить команду `git merge <название ветки>` из ветки куда нужно подтянуть изменения.
13. Конфликт слияния веток - это процесс когда git обнаруживает в строчке кода помеху или отличие для мержа, т.е. скажем Разработчик №1 в 55 строчке кода написал "Вася хороший человек" и закоммитил это в ветке мастер, а Разработчик №2 в 55 строчке кода своей ветки написал "Вася НЕ хороший человек" закоммитил и решил слить в мастер, гит в свою очередь обнаружил различие на 55 строчке при автоматическом слиянии и выдал сообщение Разработчику №2 о том что у нас конфликт и помоги разобраться с тем что мне делать в данный ситуации.
14. Решение конфлитка:
а. Можно руками убрать лишний код.
б. Решения в ide:   
Принять изменения входящие,   
Принять изменения которые были,   
Принять оба изменения (тогда гит перенесет строчкой ниже код второй(т.е. на 55 будет "Вася хороший человек", а на 56 "Вася НЕ хороший человек" из примера 13)).
15. Работа с удаленным репозиторием:  
>`git clone <адрес копируемого репозитория>` - скопировать > репозиторий в локальную папку;  
>`git remote add origin <адрес репозитория>` - используется для создания записи о новом подключении к удаленному репозиторию;  
>`git branch -M` - указывает какая ветка является основной  
>`git push -u origin master` - заливаем из локальной папки на репозиторий  
>`git push` - синхронизируем локальный репозиторий с репозиторием  
>`git pull` - из репозиторя в локальный репозиторий.  
>`git push --set upstream origin <название ветки от куда работаем>` - отправить репозиторий на согласование  
>`git remote -v` - показывает список подключенных репозиториев  
>`git commit -am "коммит"` - зафиксировать состояние и добавить коммит в одной коммандеф