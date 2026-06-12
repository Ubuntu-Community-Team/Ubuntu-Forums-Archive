---
title: "HansaWorld Proprietary Accounting Software Font Problem"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by hist on 2007-02-15
Hello

I'm having problems starting up the HansaWorld application. I get: 

2007-02-15 16:47 locale: nb_NO.UTF-8
2007-02-15 16:47 HansaWorld 5.2 (12) for Linux, (32-bit pointers, 64-bit file access) starting
2007-02-15 16:47 XLoadQueryFont: failed creating font set -*-lucida-medium-r-*-*-10-*-*-*-*-*-iso10646,-*-helvetica-medium-r-*-*-11-*-*-*-*-*-iso8859-5,-*-*-*-r-*-*-10,*
2007-02-15 16:47 XLoadQueryFont: failed creating font set -*-lucida-medium-r-*-*-10-*-*-*-*-*-iso10646,-*-helvetica-medium-r-*-*-11-*-*-*-*-*-iso8859-5,-*-*-*-r-*-*-10,*
2007-02-15 16:47 XLoadQueryFont: failed creating font set -*-lucida-bold-r-*-*-10-*-*-*-*-*-iso10646,-*-efont serif,-*-goha tibeb-zemen,-*-helvetica-bold-r-*-*-11-*-*-*-*-*-iso8859-5,-*-*-*-r-*-*-10,*
2007-02-15 16:47 XLoadQueryFont: failed creating font set -*-lucida-medium-r-*-*-10-*-*-*-*-*-iso10646,-*-helvetica-medium-r-*-*-11-*-*-*-*-*-iso8859-5,-*-*-*-r-*-*-10,*
2007-02-15 16:48 XLoadQueryFont: failed creating font set -*-times-medium-r-*-*-10-*-*-*-*-*-iso10646,-*-times-medium-r-*-*-11-*-*-*-*-*-iso8859-5,-*-*-*-r-*-*-10,*
2007-02-15 16:48 XLoadQueryFont: failed creating font set -*-times-bold-r-*-*-10-*-*-*-*-*-iso10646,-*-times-medium-r-*-*-11-*-*-*-*-*-iso8859-5,-*-*-*-r-*-*-10,*
2007-02-15 16:48 XLoadQueryFont: failed creating font set -misc-fixed-bold-r-*-*-10,-*-*-*-*-*-*-10,*
2007-02-15 16:48 Exit

..when trying to start the application. 

I try: 

#xlsfonts -fn -*-lucida-medium-r-*-*-10-*-*-*-*-*-iso10646
xlsfonts: pattern "-*-lucida-medium-r-*-*-10-*-*-*-*-*-iso10646" unmatched

..and then, with just appending an asterisk: 

xlsfonts -fn -*-lucida-medium-r-*-*-10-*-*-*-*-*-iso10646*
-b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso10646-1
-b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso10646-1
-b&h-lucida-medium-r-normal-sans-10-100-75-75-p-58-iso10646-1

So, I know that I've managed to install the font, but ubuntu seems to append a "-1" on the font name. 

Any pointers as to what I can try?. I've finally managed to get away from windows, but this accounting software is keeping me from migrating completely. 

Thank you in advance for your help;)

EDIT: I'm running ubuntu edgy with gnome

---

### Post by hist on 2007-02-23
Well, I tested this on ubuntu feisty and it now works. I really would like this is work in edgy. Any pointers as to where I may ask for help regarding this?.

---

### Post by hist on 2007-03-04
Running feisty now so I guess all is well.

---

