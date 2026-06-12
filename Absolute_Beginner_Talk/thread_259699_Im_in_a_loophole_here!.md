---
title: "Im in a loophole here!"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-09-17
So (supposedly) I got java installed correctly, I have all the boxes marked in the Package Manager.When I try to use any apt-get command, it tells me this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

And when I do "sudo dpkg --configure -a" it tells me this:


Setting up j2sdk1.4-doc (1.4.2.02-1ubuntu3) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    j2sdk-1_4_2-doc.zip j2sdk-1_4_0-doc-ja.zip j2sdk-1_4_2-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.



I really need some help here this is driving me nuts!!

---

### Post by gn2 on 2006-09-17
My suggestion would be to let Automatix take care of it for you.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by voodoonirvana on 2006-09-17
Thanks for the suggestion, Ill definetly check into that. I read the FAQs  but im not sure if I fully understand. Is Automatix an entire GUI? Or is it just an installer interface?

---

### Post by gn2 on 2006-09-17
You need to go to the webpage, click Install (under main mnu section at left of page) Then click on option 3 to run the automatic install routine by copying and pasting into a terminal window.
To open a terminal window, click "Applications" "Accessories" "Terminal"

Once Automatix has been installed it will appear in your Applications menu.

---

### Post by voodoonirvana on 2006-09-17
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: Type 'servers.' is not known on line 24 in source list /etc/apt/sources.list


That is what I get when I get to the third code. I think I may have messed with my sources.list or something.

---

