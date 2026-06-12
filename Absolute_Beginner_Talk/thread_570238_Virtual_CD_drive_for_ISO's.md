---
title: "Virtual CD drive for ISO's?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-10-08
I want to make an ISO and install it from a virtual cd drive? Is that possible? What is the best program for making ISO's and making a virtual drive?

---

### Post by pay on 2007-10-08
To create a iso from a cdrom (change /dev/cdrom to your cdrom)```
sudo umount /dev/cdrom
readcd dev=/dev/cdrom f=file.iso
```To mount an iso ```
sudo mkdir /media/iso
sudo modprobe loop
sudo mount -t iso9660 -o loop file.iso /media/iso/
```

---

### Post by dwhitney67 on 2007-10-08
If you are looking to make an ISO from a collection of files/folders on your system, try the *mkisofs* command.  That's what I use to make ISOs that I write to CD-Rs.

---

### Post by ~~Tito~~ on 2007-10-08
No, like from a bunch of files, like I dumped the data of I game I had a while back and I want to make it an ISO. In windows Nero can make virtual drives and u can use that to install ISO's with out CD's. Is there a way to do this.

---

### Post by ~~Tito~~ on 2007-10-08
> **dwhitney67 said:**
> If you are looking to make an ISO from a collection of files/folders on your system, try the *mkisofs* command.  That's what I use to make ISOs that I write to CD-Rs.

Wow, U answered after I submitted. Ok, I will try it.

---

### Post by dwhitney67 on 2007-10-08
Here's an example of the usage of mkisofs:

```
 mkisofs -o myISO.iso -b boot/grub/iso9660_stage1_5 -c boot/boot.catalog \
                -no-emul-boot -boot-load-size 32 -boot-info-table -l \
                -allow-leading-dots -J -R -r target
```

You might not need every option as specified above.  In my usage, I am making a Linux bootable CD-R.  I suggest you plow thru the man-page for mkisofs to get a better understanding of the options you need.

---

### Post by ~~Tito~~ on 2007-10-08
Hmm, Is there a way to boot the ISO with out burning it, because I have no black CD's to put it back on.

---

### Post by kvonb on 2007-10-08
......and if you'd rather do it the GUI way:

Search in Synaptic for:

gmountiso
genisoimage
kiso


..plus there are converters for other formats:

nrg2iso
mdf2iso
ccd2iso

:)

EDIT:  oops, genisoimage is NOT GUI, sorry :(

---

### Post by ~~Tito~~ on 2007-10-08
What about what I have been saying a virtual drive so I can use the ISO as a Virtual CD and Install it?

---

### Post by ~~Tito~~ on 2007-10-08
How would I launch kiso? Go in the terminal and say kiso?

---

### Post by dwhitney67 on 2007-10-08
If you have a bootable ISO, then you could use VMware.  If it is merely an ISO containing data, then use **pay**'s advice on creating a loop-back device (although I do not believe the modprobe step is necessary).

---

### Post by ~~Tito~~ on 2007-10-08
So, like if I had made an ISO of windows before ubuntu and aved it and have the CD key how would I go around to use it in VM ware server? Thats why I am asking about a virtual drive?

---

### Post by dwhitney67 on 2007-10-08
I'm too lazy to power up my Ubuntu system that has VMware on it, but I do know that once you have started VMware and created a new virtual system, that you can change the default behaviour of booting from a CD to booting from an ISO.

Look at the properties for the virtual system, or more specifically, the properties for the CD/DVD drive.  There you can change to use an ISO, and even specify the location of the ISO image you want to use.

---

### Post by ~~Tito~~ on 2007-10-08
Cool, thanks, but Iinstalled it but when I try to run something in its terminal it quits. . .

---

### Post by ~~Tito~~ on 2007-10-08
Well It says this in the regular terminal. . .

```
tito@TITOS-LAPTOP:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/home/tito/bin/vmware-config.pl.

tito@TITOS-LAPTOP:~$ 


```

And when I put thta I get this:```
tito@TITOS-LAPTOP:~$ /home/tito/bin/vmware-config.pl.
bash: /home/tito/bin/vmware-config.pl.: No such file or directory
tito@TITOS-LAPTOP:~$ cd /home/tito/bin/vmware-config.pl.
bash: cd: /home/tito/bin/vmware-config.pl.: No such file or directory
tito@TITOS-LAPTOP:~$ 

```

What do I do?

---

### Post by dwhitney67 on 2007-10-08
Beats me.  I usually run VMware from the **Applications -> System Tools** menu.  I've never tried to run it from the command line.

---

### Post by ~~Tito~~ on 2007-10-08
Well all I have is the consol for VMWare, what does yours look like?

---

### Post by dwhitney67 on 2007-10-08
See the screenshot...

---

### Post by dwhitney67 on 2007-10-08
Here's the "howto" I believe I followed to setup VMware:

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)


Correction:  I followed these [instructions]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#VMWare_Server_.2F_Workstation").

---

### Post by ~~Tito~~ on 2007-10-08
Mine doesnt load it just says loading then it goes away? What could be the problem?

---

### Post by ~~Tito~~ on 2007-10-08
Hmm, I need to uninstall it. Whats the command?

---

### Post by dwhitney67 on 2007-10-08
I presume you mean the ISO doesn't load; in such case I can I haven't a clue.

It's strange that you stated that you "made" an ISO of Windows.  Do you not have the Windows installation CD?  That's what I would try to use under VMware.  But since I lack the experience doing such, I can't say if that would any better.

---

### Post by ~~Tito~~ on 2007-10-08
No, No. I said it wont load, just by clicking it, I haven't used any ISO or CD yet, I want to uninstall it and do it again. Command Please?

---

### Post by dwhitney67 on 2007-10-08
I don't know the proper steps to remove VMware.  However, I came across this link that may just solve the issue you are having.  Give it a read [here]("http://www.debuntu.org/vmware-server-not-starting-after-reboot").

---

### Post by pay on 2007-10-08
> **~~Tito~~ said:**
> Well It says this in the regular terminal. . .

```
tito@TITOS-LAPTOP:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/home/tito/bin/vmware-config.pl.

tito@TITOS-LAPTOP:~$ 


```And when I put thta I get this:```
tito@TITOS-LAPTOP:~$ /home/tito/bin/vmware-config.pl.
bash: /home/tito/bin/vmware-config.pl.: No such file or directory
tito@TITOS-LAPTOP:~$ cd /home/tito/bin/vmware-config.pl.
bash: cd: /home/tito/bin/vmware-config.pl.: No such file or directory
tito@TITOS-LAPTOP:~$ 

```What do I do?Try removing the fullstop```
/home/tito/bin/vmware-config.pl
```you might need to make it executable ```
chmod +x /home/tito/bin/vmware-config.pl
./home/tito/bin/vmware-config.pl
```

---

