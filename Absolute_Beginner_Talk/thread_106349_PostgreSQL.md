---
title: "PostgreSQL"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Enter on 2005-12-20
ok so setted it up in synaptic how do i configure it now?
with mysql you do this comand to create the root acc password
mysqladmin -u root password 'pass'
now how do i do that in PgSQL
i looked in the manual and didnt find anything
and Wiki has nothing on PgSQL

---

### Post by prammy on 2005-12-20
You have to switch to the postgres user initially.

su - postgres
createuser username (use your username)
Say Yes to creating users and databases

You can create a database with the createdb shell command.

---

### Post by Enter on 2005-12-20
ok one proble su - postgres doesnt work :D

---

### Post by tomx313 on 2005-12-20
same problem here

it says: "su: Authentication failure"

suggestions?

---

### Post by Enter on 2005-12-21
it gives me 

Unknown id: postgres

:lol:

---

### Post by Juippisi on 2005-12-21
I'm not familiar with PostgreSQL, but what "sudo postgres" says? I think Prammy ment that first su root and then command postgres. Not sure.

---

### Post by Enter on 2005-12-21
enter@localhost:~$ sudo postgres
Password:
sudo: postgres: command not found
enter@localhost:~$

hm but i installed it its in the phpinfo();

---

### Post by Juippisi on 2005-12-21
Type pos and press tab. It should complete the command.

Again: I'm not familiar with PostgreSQL - I can't help anymore, I think.

---

### Post by Enter on 2005-12-21
all comands that start from po

po2debconf             poff.wvdial            postfix
pod2html               pon                    postkick
pod2latex              pon.wvdial             postlock
pod2man                popclient              postlog
pod2text               popcon-largest-unused  postmap
pod2usage              popd                   postqueue
podchecker             popularity-contest     postsuper
podebconf-display-po   postalias              powernowd
podebconf-report-po    postcat                poweroff
podselect              postconf
poff                   postdrop

i see no postgresql commands there :(

---

### Post by Juippisi on 2005-12-21
Hmm, maybe your path is wrong, but I doubt. Try still command "sudo su postgres".

I suggest you to check this page out: 
[http://oakley.bioinformaticsonline.co.uk/archives/2005/11/09/postgresql-on-ubuntu-linux-how-to/](http://oakley.bioinformaticsonline.co.uk/archives/2005/11/09/postgresql-on-ubuntu-linux-how-to/)
"PostgreSQL on Ubuntu Linux - How To"

---

### Post by Juippisi on 2005-12-21
Oh, and install packages postgresql-8.0, postgresql-client-8.0, pgadmin3 and pgadmin3-data (sudo apt-get install postgresql-8.0 postgresql-client-8.0 pgadmin3 pgadmin3-data)

And check that page out ;-)

---

### Post by Enter on 2005-12-21
thank you fellow web developer
now i can make scripts with with PgSQL

---

### Post by tomx313 on 2005-12-21
yes! really thanks man!  
that link saved me!!
NOW IT ALL WORKS   :D :D 

thanks!

---

