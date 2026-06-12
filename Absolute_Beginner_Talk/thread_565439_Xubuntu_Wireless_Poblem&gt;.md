---
title: "Xubuntu Wireless Poblem&gt;"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by rtr86 on 2007-10-02
Hi all,

I recently moved from Ubuntu (7.04) to xubuntu :)

I had wireless working perfectly on Ubuntu but am having problems getting my WMP54GS to work using NDISWAPPER.

I have followed instructions from my wireless install of ubuntu on this xubuntu setup and I am having trouble blacklisting the generic driver, i used this code:

```
sudo -s
echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
exit
```  

Which although worked perfectly on Ubuntu get an 'Permission Denied' on Xubuntu. I think it is the problem which is causing my wireless not to work.

Hope all makes sense, any help appriciated.

Thanks

---

### Post by Seisen on 2007-10-02
You can add it manually to /etc/modprove.d/blacklist if that isn't working.

---

### Post by rtr86 on 2007-10-02
Can you explain how please? 
Thanks

---

### Post by rtr86 on 2007-10-02
Any help appriciated.

---

### Post by rtr86 on 2007-10-03
1 Last BUMP :(

---

### Post by hyper_ch on 2007-10-03
(1)
```

gksu mousepad

```

(2) open */etc/modprobe.d/blacklist* in it

(3) on a new line add: *blacklist bcm43xx*

(4) Save the file and exit mousepad

---

### Post by dwhitney67 on 2007-10-03
Edit the file using this command:
[FONT="Courier New"]
$ sudoedit /etc/modprobe.d/blacklist[/FONT]

On my system, the vim editor is launched.  If you do not know vim, then try:
[FONT="Courier New"]
$ gksudo gedit /etc/modprobe.d/blacklist[/FONT]

---

### Post by rtr86 on 2007-10-03
Thanks guys :) Will try asap.

---

### Post by natman on 2007-10-03
the thing you have to modify needs  "sudo" premission, so just open a terminal and type
sudo nano "file you need to change"
then enter password and add the line to the text file, and close and save ( you can use any text edtior, kate,gedit or nano up to you )
that should work

---

### Post by rtr86 on 2007-10-03
Thanks for replys, that driver is definately blacklisted now but I still cant get wireless :( Dont know what else todo. Does xUbuntu use other native drivers by default? My wifi card is Linksys WMP54GS.

Thanks

---

### Post by rtr86 on 2007-10-03
:)^

---

### Post by rtr86 on 2007-10-05
Any help appriciated

---

### Post by rtr86 on 2007-10-06
One last BUMP as I really dont know what else to try. 

I have installed NDISWAPPER and my linksys WMP5GS driver but internet connection is still not working. I have blacklisted the 'bcm43xx' which caused a problem on Ubuntu, i thought xubuntu would of been the same?

Thanks

---

### Post by bapoumba on 2007-10-06
I am not an expert with networking, even less with wireless. Should work the same whether you are using GNOME or Xfce.
Can you post the output to:
```
cat /etc/network/interfaces
ifconfig
```
So that others can help you.

---

