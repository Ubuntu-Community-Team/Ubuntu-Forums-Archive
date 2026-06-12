---
title: "GRUB GRUB problem..."
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by pnx031 on 2007-05-23
I have 1 hard disk which is 120gb in space in which i have an NTFS partition where I keep windows xp a Linux3 20gb and a swap of 1gb. I have successfully installed Ubuntu and I am currently logged in through them, ie I haven't done anything wrong with the installation. It's the first time I tried Linux and so I am confused. I know Grub is the boot loader from where I choose where to boot. But it seems as though Grub has a bug OR was not installed successfully. I tried reinstalling Ubuntu that's formatting again and installing through live cd but I still get the same problem. Where you wait to get to the Grub menu to choose boots, I get a repetitive GRUB GRUB GRUB msg which goes everywhere and repeats itself. I am trying to understand how to reinstall Grub and I've read all the help links in the absulute beginner talk but I dont seem to find anything to match my case. 
The only way for me to manage to boot to windows and OR linux is insert the live Ubuntu disk and choose boot from first harddisk :S

Can you help me please? I am confused. I dont seem to find where I went wrong.

---

### Post by gn2 on 2007-05-23
Maybe this might help : [http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by pnx031 on 2007-05-23
thanks i'll try it out :)

---

### Post by pnx031 on 2007-05-23
I tried everything. 
I did the step by step guide on Grub. It seems tho as if Grub has a problem with my drive. I uninstalled Grub and I am now back in windows. Maybe I can manually EDIT my boot.ini and include linux. I am confused as I can't use Grub to do this. Grub installs perfectly fine but I get the GRUB GRUB GRUB GRUB GRUB ERROR all over my screen which never never stops. =/

can't I just manually edit my boot.ini file to include Ubuntu? :S

---

### Post by antoz on 2007-05-23
[http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)

---

### Post by pnx031 on 2007-05-24
```
Code Listing 7.1: Grub Output

GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB
  GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB
...

Solution

According to airhead this can be caused by having your bios detect your disks automatically. Try to set your bios entry to User Type HDD.

Another possibility is that you had Grub installed on your MBR and tried reinstalling it (for instance due to hard disk changes) but used the wrong setup and root commands. 
```

Ehmm Yes... there is not such an option in my bios. I set up my hard disk manually but still I get the same problem. I tried reinstalling but still stuck. :S
Is there any other booting program?
when I select to boot from the livecd option - boot from hard disk. it works just fine :S

---

### Post by gn2 on 2007-05-24
> **pnx031 said:**
> [code]
Is there any other booting program?


Yes there's Gag: http://gag.sourceforge.net/

I've never had a booting problem that wasn't cured by reading this: http://users.bigpond.net.au/hermanzone/

---

### Post by pnx031 on 2007-05-24
do i have to uninstall grub? how do i uninstall it if i have to.
and is gag as good as grub? ;o

---

### Post by pnx031 on 2007-05-24
could it also be a problem that i have configured a floppy disk and i have removed it that causes the grub problem? 

also the 2nd time I tried to reinstall it I got this error

```
# grub

Probing devices to guess BIOS drives. This may take a long time.

```

: ( i am a sad panda :(

---

