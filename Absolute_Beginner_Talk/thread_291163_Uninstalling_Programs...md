---
title: "Uninstalling Programs.."
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by frizzl on 2006-11-02
well i managed to install automatix 2, however i am using edgy and it is apparently not supported for the 64 bit version...

i have installed the dapper version (by mistake...) and i am trying to uninstall it. however, the program is not found anywhere in my Add/Remove options.

any help would be appreciated :)

---

### Post by Klaidas on 2006-11-02
Well, it depends on what install method you have used.

Try these:
> sudo apt-get remove program
> sudo dpkg -r program

---

### Post by frizzl on 2006-11-02
thankyou very much, that solved it

the program name automatix2 worked :)

then used sudo apt-get autoremove to get rid of anything else left over

thankyou very much!

---

