---
title: "help with installation"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by invader980 on 2006-01-17
Im brand new to linux ubuntu was my firt try @ it  and i have absolutley no idea what im doing ....lol never the less i got threw the installation ... but i ended up at a command prompt prompting me for my user name n pass .. once i login there no graphical interface @ all.... im not 100% sure what thsi means.

it was the equivalent to starting up in dos on windows... so im lost. i did catch a few errors i saw tho:

"missing kernel or user mode drivers"  - i believe is what it said when i loaded in recovery mode

"acpi: unable to locate rsdp" - on normal boot up

thanx in advanced for any hep u guys can provide ... i know u hate getting these types of messages ( when the user has no idea what there doing) lol

---

### Post by mustang on 2006-01-17
Hmm I'm not sure about the errors but I think I might be able to help you out with why it's not coming up with a graphical interface.

Once you've logged in at that command prompt you are talking about, try ```
 sudo gdm
```

If that's a no-go, try ```
sudo apt-get install ubuntu-desktop
```

---

### Post by hen3rz on 2006-01-17
Did you type Server at the start of the installation?

Because if you did I would suggest doing the install again but this time don't type in Server at the start, just leave it blank. There is a way to load the gui using apt-get while in the server install but by doing this you miss out on alot of basic things that would make your ubuntu experience alot easier.

If you are sure you didnt type "server" at the start of the install then I'm not suite sure what went wrong.

---

### Post by invader980 on 2006-01-18
[QUOTE=hen3rz]Did you type Server at the start of the installation?

Because if you did I would suggest doing the install again but this time don't type in Server at the start, just leave it blank. There is a way to load the gui using apt-get while in the server install but by doing this you miss out on alot of basic things that would make your ubuntu experience alot easier.

If you are sure you didnt type "server" at the start of the install then I'm not suite sure what went wrong.[/QUOTE]


 thats actualy exsactly what i did .... i figured that that would be hte main difference so i reinstalled with out typing server ... im implamenting the first idea as we speak

---

### Post by invader980 on 2006-01-18
the first command u gave me unleshed a series of errors lol the secound command gave me the following error :

"E: dpkg was interrupted , you must manually run dpkg --configure -a to correct the problem"

 when i did so it told me :
"requested operation requires superuser privileges"..

im logging in  with the user name and password i created @ installation....

also (unrelated): how do i uninstall  if i need to later on...

---

### Post by kaamos on 2006-01-18
Try
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install ubuntu-desktop
```
About sudo: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by invader980 on 2006-01-18
well i ran out of disk space .... im goin to try to install on my other computer....

will there be any problems with my current os ( windowz xp)  if i install ?

and how do i clean my other hard drive of the instalation ?

( i know i ask  alot of questions lol sorry)

---

### Post by invader980 on 2006-01-18
nvm i figured out the command thankx for the help guys im sure ill be back later

---

### Post by Sef on 2006-01-18
> will there be any problems with my current os ( windowz xp) if i install ?

The dual boot should work fine.  Read this excellent tutorial on how to dual boot:

[http://users.bigpond.net.au/hermanzone/index.htm]("http://users.bigpond.net.au/hermanzone/index.htm")

> well i ran out of disk space

Do a server install and download a lightweight window manager, e.g. fluxbox, icewm, xfce.

From the server terminal:

1) sudo apt-get update

2) sudo apt-get install (window manager)-desktop

3) To start type:  startx  (works like win in Windows.)

---

### Post by invader980 on 2006-01-20
thanx for the help .... i switched computers ..... downloaded partition magic .... got threw the installation  ( i was getting excited lol ) installed grub everythig was goinf well:
 then on my very first boot  i froze up on :
"starting hotplug subsystem...... "

any suggestion or explanation  .... lol im determained to install this goin on the 3rd day lmfao :D

---

