---
title: "Apache can't read PHP file"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by phyxsly on 2007-04-22
I don't know if this is the right place for my question. Anyway, here is the problem,

I just installed feisty on my laptop. Then after, i installed Apache and PHP. Accessed the localhost through firefox and it works perfectly well. But when I tried to open/access a php, it always open a dialog box asking me to open or save the php file. I have used edgy and i never encountered this kind of error.

Can anyone please help?

Thanks.

---

### Post by mbspark on 2007-04-22
I had the same problem when I had apache and apache2 installed. They weren't working right together. I went to synaptic and made sure that only apache2 was installed and I removed regular apache and it worked great. So now my setup is apache2 and php5

---

### Post by az on 2007-04-22
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

You need the libapache2-mod-php5 package for apache2 to use php5.

---

### Post by nunomp on 2007-04-22
I have the same problem.. i had two running servers (one edgy and one dapper, which i keep). Setup: apache2 + php5 + mysql . With feisty it took longer to setup apache2 because userdir module was not enabled by default (I don't get it...) and refuses to process php files. I have the libapache2-mod-php5 installed.. any news?

EDIT: solved after a purge and reinstall.. this feisty has some crazy bugs..

---

