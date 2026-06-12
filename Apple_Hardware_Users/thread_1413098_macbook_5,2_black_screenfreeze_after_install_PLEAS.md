---
title: "macbook 5,2 black screen/freeze after install PLEASE HELP"
date: 2010-02-22
forum: Apple Hardware Users
---

### Post by petejohnson on 2010-02-22
I have an nvidia macbook 5,2 with upgraded ram. looking through these forums I have been able to successfully get the live cd to finally install with a triple boot.. However, when I choose ubuntu (Which refit thinks is legacy) It says "grub loading" then it gives me options. I choose to load linux.
I get a cursor and then it freezes/goes black. 
This is my first time using linux and so I am very new at this. I have always used windows or osx. 
I dont know even how to enter commands into it.
Thank you in advance for any help.

---

### Post by amsterdamharu on 2010-02-22
> I dont know even how to enter commands into it.
So you get a command prompt? If so you might try installing all the updates. Run the following commands:
```

sudo apt-get update
sudo apt-get upgrade
```Does the boot menu have a "recovery" choice? If it does choose that one and choose fix x, this will try other video card settings. When you get ubuntu to boot do an update and try the nvidia driver (under system -> administration -> hardware drivers).

If you don't have a recovery choice you can try the ubuntu menu entry in grub and press e (not enter) to edit the entry. There is a line starting with kernel .... or linux ... at the end of the line add xforcevesa.

If that doesn't work then reboot and add noacpi

---

### Post by wheeeler on 2010-02-25
On my MacBook 5,2 I hang unless I boot with acpi=off.  I read somewhere that you could keep ACPI if you sacrifice a core (maxcpus=1), but I don't want ACPI that badly.

---

