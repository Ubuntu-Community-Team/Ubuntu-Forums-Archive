---
title: "Best database"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by pachjo on 2006-10-10
Can anyone advise which is the most appropriate database to use in Ubuntu please?

I want to write very small home use application using python and a GUI similar to what you would get if you wrote an Access application.

Any tips?

---

### Post by amo-ej1 on 2006-10-10
If you want something that behaves like a file you should look at things like gdbm ( [http://www.gnu.org/software/gdbm/](http://www.gnu.org/software/gdbm/) ). If you want a 'real' database you  should take a look at mysql and postgresql. Most depends on your needs. Since there is no license penalty or such you can pick a small one, or a big one ;) but will require about an equal effort to get started i'd say.

---

### Post by pachjo on 2006-10-10
Thanks, I was looking at mysql but was not sure if it would fit my purpose.

I then came across a link to SQLite which attracted my attention as it is serverless which basically is all I need so will see if that will work.

I also found a link to something called SQLObject which is where I found the link for SQLite.

Thanks

---

### Post by Marsolin on 2006-10-10
What you probably need is a [database front-end]("http://linuxappfinder.com/databases/editorsinterfaces"). That's what is like Access. They can use [MySQL]("http://linuxappfinder.com/package/mysql-server") of another database as the back-end.

[Knoda]("http://linuxappfinder.com/package/knoda"), [Kexi]("http://linuxappfinder.com/package/kexi"), [Glom]("http://linuxappfinder.com/package/glom"), and [Base]("http://linuxappfinder.com/package/openoffice.org-base") are a few you could check out.

---

### Post by pachjo on 2006-10-11
I think I did not detail my original post effectively?

I want to create a GUI application similar to how you would do one in say Access.

I don't mean to have an all in on development suite like Access which provides the database, GUI and code as I don't think that is available in Linux?  I did look at base but there is no code for it?

So what I am trying to get to grips with is to write code in python, GUI using a GUI development tool and a database tool, possibly SQLite and then link all three together using the python bit.

---

