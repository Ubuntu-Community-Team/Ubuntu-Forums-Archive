---
title: "Failed to execute child process &quot;vmware&quot; (No such file or directory)"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by BlackMambo on 2006-07-09
After installing VM Ware, when I click on the menu item (Applications/System Tools/VM Ware Server Console), I get a

[B][COLOR="Red"]Could not launch menu item

Details: Failed to execute child process "vmware" (No such file or directory)
[/COLOR][/B]
Anyone know what could be the problem?

---

### Post by BlackMambo on 2006-07-10
Anybody know how to fix this?

---

### Post by wowshailen on 2007-06-17
Me too, I'm frustrated. Sa many people use ubuntu and vmware, yet noone bothers to think why such a problem arises. I tried to uninstall and re-install,but to no avail.

I downloaded the latest Vmware workstation 6 and didnt work on my machine. Is the package faulty?

Can anyone help?

---

### Post by wowshailen on 2007-06-17
Ok, I got it by myself..

Install vmware via the terminal. Then run vmware from the terminal.

user\bin\vmware
vmware

I am currently looking for a way to modify the "bug" that occurs when u click on Systerm Tools>Vmware Workstation ; right click, edit link does not work as straight forward as in Woes..:)

---

### Post by wowshailen on 2007-06-18
Hi Black Mambo,

Try uninstalling Vmware:

cd /user/bin/vmware
sudo ./vmware-uninstall.pl

Then reinstall again.

[DON't CHANGE DEFAULT LOCATIONS!!! **]

Everything shud be okay as frm now :)

---

