---
title: "?? how can i change the zone for update ?"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Janoubie on 2006-11-24
...
when i install ubuntu in other pc .. i forget to change the zone ..
then after everythhing work .. i change easly the zone form "time and zone"
but when i update still from the zone (qater) that i install it ?
it's slowly than my zone .. how can i cahnge ?

---

### Post by bollix47 on 2006-11-24
Open synaptic.

Click on settings - repositories.

Click on the arrows for "Download from" and see if you can change it from there.

---

### Post by Janoubie on 2006-11-24
thank u for replay
but
i follow your steps but there is no my zone in it ... only main sereve and usa server 
my server that i need it is Saudie arabia is my zone and speed

---

### Post by Janoubie on 2006-11-24
A N D 

how can i add fonts :)

---

### Post by bollix47 on 2006-11-24
You can change the country code in your sources list using an editor.

gksudo gedit /etc/apt/sources.list

click on search - replace

Search for qa-
Replace with sa-

Save your file and exit

Load synaptic and click on reload

---

### Post by Janoubie on 2006-11-24
what about FONT ? :$

---

### Post by bollix47 on 2006-11-24
Try using the search button for "font" (without the quotes) in synaptic.

---

### Post by Janoubie on 2006-11-24
mr bollix ...

I search but for what .. i need add thoma to fonts folder
i try copy it but not work

---

### Post by kenweill on 2006-11-24
Open up a terminal then run the command

sudo gedit /etc/apt/sources.list

then search for the lines thats having a url with "http://qa" and replace it with "http://".

qa is country specific. I just dont know what qa is. But here in our area, "ph" for philippines.

Deleting the "qa" revert it to fetch updates from the main repository.

---

### Post by Janoubie on 2006-11-24
qa = qater 
.. thx it's work now but in anther way any1 tell me how can add new fonts ?

---

### Post by kenweill on 2006-11-24
That should be in a separate thread.
There have been alot of threads regarding adding fonts. Try to search for it.

---

### Post by CaveRat on 2006-11-24
Check out Automatix2. It can install extra fonts.

---

### Post by Janoubie on 2006-11-24
> **kenweill said:**
> That should be in a separate thread.
There have been alot of threads regarding adding fonts. Try to search for it.

I don't write befor search .. I really search but no simple use .. i'm try now translte helping in arabic language in other arabic forum ..
ok i'm sorry for quation .. i'm sorry

---

### Post by kenweill on 2006-11-24
Dont.
You dont have to say sorry.
What fonts are you trying to install?

---

### Post by Janoubie on 2006-11-24
thoma and bold thoma for arabic

---

### Post by kenweill on 2006-11-24
> **Janoubie said:**
> thoma and bold thoma for arabic

Try:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Extra_Fonts](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Extra_Fonts)

---

### Post by bollix47 on 2006-11-24
If you mean *tahoma* then I believe it is microsoft property and you may not be able to get it for linux.  There may be a way to copy from a windows installation but not sure.

---

### Post by kenweill on 2006-11-24
> **bollix47 said:**
> If you mean *tahoma* then I believe it is microsoft property and you may not be able to get it for linux.  There may be a way to copy from a windows installation but not sure.

Yes. There is.
Open up Nautilus or Konqueror then in the address bar(of konqueror) type "font://" paste your .ttf(true type font) files from windows into that directory.

---

### Post by bollix47 on 2006-11-24
Yes I agree that they can be copied.

Look [_here_]("http://wiki.linuxquestions.org/wiki/Installing_Windows_fonts#GNOME_users") for instructions.

btw - it's font**s**://

---

### Post by drphilngood on 2006-11-24
You may find this thread, [How to install fonts in Ubuntu?]("http://ubuntuforums.org/showthread.php?t=275202"), useful as well.

---

