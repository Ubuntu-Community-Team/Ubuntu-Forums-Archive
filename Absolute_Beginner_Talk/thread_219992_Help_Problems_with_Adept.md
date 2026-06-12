---
title: "Help: Problems with Adept"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by bstreet85 on 2006-07-20
Hi all,

I was trying to open up adept in order to get new packages, and every time I do, I'm presented with a message that looks like this:

"You will not be able to change your system settings in any way because another program is using the packaging database. Please close before trying to open again"

The problem is that I don't have any other applications running when this happens. Any suggestions?

---

### Post by kingmonkey on 2006-07-20
Open up a terminal and type:

```
 sudo apt-get update
sudo apt-get upgrade
sudo apt-get install the.program.you.want.to.install

```

If it doesnt work type any error messages here.

---

### Post by bstreet85 on 2006-07-20
Here's what it said:

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by kingmonkey on 2006-07-21
run:

```
sudo dpkg --configure -a 
```

---

### Post by susa on 2006-07-21
not sure if related to OP but sometimes when I install items which call for a change between gdm or kdm, there is hidden window in adept behind the "display details" which is asking for selection and Ok

found out that once I click the "details" and make the selection, install proceeds and everything is fine

---

