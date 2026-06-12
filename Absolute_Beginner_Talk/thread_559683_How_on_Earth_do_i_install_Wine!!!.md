---
title: "How on Earth do i install Wine!!!???"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Wee_Guy on 2007-09-25
I have Ubuntu running through Qemu on my Intel Mac.
I want to install Wine and use it.
For the life of me, [SIZE=4]I CAN'T GET IT TO WORK!!!!!!![/SIZE] :-s :-s :-s :-s
[SIZE=4]
THIS THING IS DRIVING ME NUTS!!![/SIZE] :mad:  ](*,):mad:(i don't even like nuts)

[For the record, i have no idea how to install a normal app on Ubuntu, i *think* that it may involve Terminal, but i have no idea how. I tried to run the script labeled "setup.py" that appeared on the folder on my desktop after i downloaded it from the app manager.]

[SIZE=7]_**HELP!**_[/SIZE][SIZE=4](It's for the safety of my forehead--and keyboard!)[/SIZE]

---

### Post by ThRixXx on 2007-09-25
Are u running linux ubuntu Feisty Fawn ?

---

### Post by Vadi on 2007-09-25
Applications - Add/remove.

Search for "wine".

Click the checkbox beside it, and select "Apply".

Enjoy!

---

### Post by LaRoza on 2007-09-25
```

sudo aptitude install wine

```

---

### Post by weedeatr on 2007-09-25
Try this link and follow the instruction (this wil only work if you have synaptic package manager)


link:[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)



once you have finished that go to system-administrator-synaptic package manager search for wine and install it

:)

---

### Post by Kilz on 2007-09-25
> **Wee_Guy said:**
> I have Ubuntu running through Qemu on my Intel Mac.
I want to install Wine and use it.
For the life of me, [SIZE=4]I CAN'T GET IT TO WORK!!!!!!![/SIZE] :-s :-s :-s :-s
[SIZE=4]
THIS THING IS DRIVING ME NUTS!!![/SIZE] :mad:  ](*,):mad:(i don't even like nuts)

[For the record, i have no idea how to install a normal app on Ubuntu, i *think* that it may involve Terminal, but i have no idea how. I tried to run the script labeled "setup.py" that appeared on the folder on my desktop after i downloaded it from the app manager.]


[This guide ]("http://cutlersoftware.com/ubuntuinstall/")will help you learn how to install applications.
It may be that you will have problems after you install it. This link will help you use wine.  Wine is not an application you start by clicking on an icon.[ For more info read here.]("http://tghc.org/winefaq.html")

---

### Post by Wee_Guy on 2007-09-25
OK, i ran the code LaRoza posted and visited the links Kiltz posted. The [something] package manager says it's installed. Is it finished or is there anything else that i need to do?

---

### Post by Wee_Guy on 2007-09-25
So i'm trying to install lemmings via the CD, i've tried making a diskimage of it on OS X and setting it as the CD on Qemu, but ubuntu tinls it's a blank CD-ROM (it opens CD/DVD creator). How do i get the files from the CD/diskimage of the CD onto the virtual Ubuntu machine?

---

### Post by weedeatr on 2007-09-25
i think it is a problem with the cdrom or reader

---

### Post by Wee_Guy on 2007-09-25
OS X manages to read it fine, i made a disk image of it, but Ubuntu, running through Qemu, opens CD/DVD creator when i click on the CD-ROM icon.

---

### Post by funpop on 2007-09-25
uhm try to navigate to your cdrom directory in the terminal:
```

cd /media/cdrom
```

and then run ```
wine setup.exe
``` or whatever installer you find there

---

### Post by stchman on 2007-09-25
> **Wee_Guy said:**
> I have Ubuntu running through Qemu on my Intel Mac.
I want to install Wine and use it.
For the life of me, [SIZE=4]I CAN'T GET IT TO WORK!!!!!!![/SIZE] :-s :-s :-s :-s
[SIZE=4]
THIS THING IS DRIVING ME NUTS!!![/SIZE] :mad:  ](*,):mad:(i don't even like nuts)

[For the record, i have no idea how to install a normal app on Ubuntu, i *think* that it may involve Terminal, but i have no idea how. I tried to run the script labeled "setup.py" that appeared on the folder on my desktop after i downloaded it from the app manager.]

[SIZE=7]_**HELP!**_[/SIZE][SIZE=4](It's for the safety of my forehead--and keyboard!)[/SIZE]

Follow my procedure:

[http://www.stchman.com/install_wine_IE.html](http://www.stchman.com/install_wine_IE.html)

That is it.

---

### Post by weedeatr on 2007-09-26
if you click on the .exe file or setup file the just say run with 'wine'


:)

---

### Post by Wee_Guy on 2007-09-27
The latest problem is that now the virtual comp has dissapeared from Q's list. i can open it via the diskimage of the machine, but it isn't on the list of virtual machines on Q. I'm not sure whether it is saving properly or not yet.

---

### Post by Wee_Guy on 2007-09-27
I tried the code that funpop posted but when i run the Wine bit, it says that the module is not found. I have checked it, tried running both the program (Lemmings :rolleyes:) and the autorun program, both bring the same results.
I think that the problem is that it isn't actually seeing the CD. i know *how* to run a windoezer app via wine, but Ubuntu can't/isn't seeing the disk image properly. I'm trying to set up a network between the virtual machine and the Mac itself, but haven't got very far so far...

---

### Post by Wee_Guy on 2007-09-27
Now that ive downloaded a couple of windows apps and installed them, how do i find them?

---

