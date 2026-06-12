---
title: "ati drivers install help?"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by buckskinmike on 2006-09-10
hey im trying to install the new ati drivers fallowing method 2 of this guide 
[http://www.wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually](http://www.wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually)

ive disabled fgl rx and when i try to run this 
"sudo apt-get update
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)"
it connects to a bunch of servers then says i have 8 files i need to download do i want to continus y/n. no matter what i put in it automatically goes to abort when i press enter. anyone know how i can get these updates to download?

---

### Post by meng on 2006-09-10
Are you entering those 3 commands one at a time? I assume you are, and even if you weren't I'm not sure why it would make a difference. Anyway, as I'm sure you appreciate, the computer should not abort the operation unless you enter N. I can't explain why it doesn't seem to work.

---

### Post by buckskinmike on 2006-09-10
i was entering them all at once. i tried one at a time and it worked. thanks alot:)

---

### Post by meng on 2006-09-10
Glad to hear it. I'm guessing that by entering them all at once, you filled the "text buffer" and that caused apt-get to abort because it interpreted this as a "non-yes" response.
If you want to enter more than one command, you should separate them by &&
e.g.
sudo apt-get update && sudo apt-get upgrade

---

