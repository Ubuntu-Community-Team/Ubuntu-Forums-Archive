---
title: "dual boot Vista from grub"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by mouseboyx on 2007-03-19
ubuntu 6.10 - I just installed ubuntu for x64 and i need to restore the boot loader for windows vista i have no instalation cd and i cannot boot from a usb i have no floppy drive and i can only boot from HD and     CD When i select windows vista from the grub boot menu it goes to the screen with the little scrolling bar and stays there indefinatly i realy need help because if i dont my brother will kill me because he doesnt like ubuntu and i cant get my wireless card f57000 belkin card to work on ubuntu 6.10

---

### Post by LanDan on 2007-03-19
nice, you're in trouble now ;)

ubuntu starts?

if you type "fixmbr" it will remove grub and you will start directly to windows

---

### Post by nudnik on 2007-03-19
> **mouseboyx said:**
> ubuntu 6.10 - I just installed ubuntu for x64 and i need to restore the boot loader for windows vista i have no instalation cd and i cannot boot from a usb i have no floppy drive and i can only boot from HD and     CD When i select windows vista from the grub boot menu it goes to the screen with the little scrolling bar and stays there indefinatly i realy need help because if i dont my brother will kill me because he doesnt like ubuntu and i cant get my wireless card f57000 belkin card to work on ubuntu 6.10

We will hold services for you after you are gone:mrgreen: 

Make a CD which boots into DOS. Access the HD on which Vista is installed and type the following:

fixmbr

That works for XP. Remember Vista is Evil, much Eviller than XP and may present weird problems. OK, who am I kidding? It WILL present weird problems, but hopefully not accepting the old XP boot record fix wont be one of them. 

If things dont work out, I know a great funeral director.

---

### Post by Najand on 2007-03-19
In ubuntu, open a terminal (Applications => Accessories => Terminal) and copy/paste /boot/grub/menu.lst 
and the output  of the following command:
```

sudo fdisk -l

```

---

### Post by mouseboyx on 2007-03-19
Ill try that

---

### Post by mouseboyx on 2007-03-19
It says that my permission is not allowed or something when i try to navigate to the .lst file

---

### Post by mouseboyx on 2007-03-19
how do i make a dos boot cd that has fixmbr on it i did it this way [http://www.nu2.nu/bootcd/](http://www.nu2.nu/bootcd/) but the only drives that were there were Q: and R: and fixmbr is not a command for it

---

### Post by rccharles on 2007-03-19
> **mouseboyx said:**
> ubuntu 6.10 - I just installed ubuntu for x64 and i need to restore the boot loader for windows vista i have no instalation cd and i cannot boot from a usb i have no floppy drive and i can only boot from HD and     CD When i select windows vista from the grub boot menu it goes to the screen with the little scrolling bar and stays there indefinatly i realy need help because if i dont my brother will kill me because he doesnt like ubuntu and i cant get my wireless card f57000 belkin card to work on ubuntu 6.10

Fixmbr has been replaced in Vista by bootrec.

See a real persons entry:
[http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=1198446&SiteID=17](http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=1198446&SiteID=17)

See the official M$ comments.
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

Robert

---

### Post by rccharles on 2007-03-19
> **mouseboyx said:**
> ubuntu 6.10 - I just installed ubuntu for x64 and i need to restore the boot loader for windows vista i have no instalation cd and i cannot boot from a usb i have no floppy drive and i can only boot from HD and     CD When i select windows vista from the grub boot menu it goes to the screen with the little scrolling bar and stays there indefinatly i realy need help because if i dont my brother will kill me because he doesnt like ubuntu and i cant get my wireless card f57000 belkin card to work on ubuntu 6.10

I remember you do not have the install disk.  There may be a restore partition on your harddrive. You could call the manufacture and ask for a disk.

What I think you will have to do is edit the menu.lst to fix up Grub.  

See this tutorial.  Skip all that stuff about installing Vist and Ubuntu.  Skip down to the section on changing Grub.  Boot into Ubuntu.  Follow:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

........

If for some reason you cannot get anything to boot try:
It seem that your windows restore isn't re-writing the Master Boot Record MBR. You should be able to use superGrub. It doesn't use the MBR to boot Windows or any other partition. You will still have to figure out a way of restoring the MBR to windows format. I'd look around the internet for a Windows restore MBR program.

An option would be to use superGrub. This has grub on a bootable CD. In a series of menus, superGrub lets you boot any partition.

Main page:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

download page:
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

superGrub can be a little cryptic, but looking at the screenshot page helps.

[http://supergrub.forjamari.linex.org...on=screenshots](http://supergrub.forjamari.linex.org...on=screenshots)

You cursor down to the line you want.

The help line is
| ================> Windows <=============== |

You cursor down below this line and press enter.

I wrote superGrub out to cd and it worked for me. You can boot your partition even without grub on the partition.

This wouldn't be a permanent solution, but it would get you started.

---------

You could also try the Ubuntu Live cd to get a running system so you could edit menu.lst.

Robert

---

### Post by mouseboyx on 2007-03-20
Sorry i should have told you this earlier but windows vista was in the boot loader when i first installed ubutnu i can run it too but it just stays at the stupid little scrolling bars screen and nothing happens most likely when i resized the partions windows vista got screwed up i think it would be best if i get a cd from the manufacturer and restore vista to its original state. I made a recovery disk before when i first got the pc, but it does the same thing as the boot loader and i accidentally deleted the partion with the recover stuff for windows vista gee life sucks for me. i just got this thing two days ago.

I just really wish they would include Vista cds with a new computer when you buy one, but what they probably do is they have a master install cd and just buy new keys so that they don't have to use a new cd with every computer.

This would prevent every headache you just pop in the disk and restore everything.

---

### Post by WiFi Ed on 2007-03-20
> **mouseboyx said:**
> ... most likely when i resized the partions windows vista got screwed up

Exactly what happened to me when I let gpart resize my Vista partition:(  I guess Vista is touchy about things like that.

It may be fixable, but I had to restore Vista from a backup image, partition as needed in Vista, then install Ubuntu. Now all is well, and I can triple boot into XP, Vista and Ubuntu.

Best of luck to you...

Hey, my first post! I've been using Ubuntu for about a month now, and liking it more everyday:)

---

### Post by mouseboyx on 2007-03-21
i just got a windows xp install disk but it doesnt recognize any of my drives so i cant install windows xp and just ditch everything and start over. i think its because my hard drive is not ide its something else i think raid so i would have to install drivers or something before i could use it on the intalation. this is realy starting to suck.

---

### Post by nudnik on 2007-03-21
> **rccharles said:**
> Fixmbr has been replaced in Vista by bootrec.

See a real persons entry:
[http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=1198446&SiteID=17](http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=1198446&SiteID=17)

See the official M$ comments.
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

Robert

Yep. I knew it. Evil, Evil, Evil.

---

### Post by rccharles on 2007-03-22
> **mouseboyx said:**
> i just got a windows xp install disk but it doesnt recognize any of my drives so i cant install windows xp and just ditch everything and start over. i think its because my hard drive is not ide its something else i think raid so i would have to install drivers or something before i could use it on the intalation. this is realy starting to suck.

It's probably Serial ATA  ( SATA ) which is the latest drive interface.

Check in your bios. Press esc, f2, del, or some other key just after poweron.

Robert

---

### Post by mouseboyx on 2007-03-24
OK FINALLY i got a xp cd to work and it is in the process of formating a 250 gb HD which is taking an eternity but im very confident this will work i had to change sata mode to ide 
:guitar:

---

### Post by Jose Catre-Vandis on 2007-03-24
Vista gets very unhappy about having its partition resized, this is why it will not boot up, I am surprised you are not getting a BSOD! (I did when I tried this). My only solution was to reinstall Vista onto a smaller partition then install Ubuntu 2nd, grub provides the correct entry to boot Vista. I doubt whether you can "go back" i.e. uninstall Ubuntu, return the Vista partition to its original size etc?

Since discovered how to deal with all this, look here:

[http://www.ubuntuforums.org/showthread.php?p=2353114#post2353114](http://www.ubuntuforums.org/showthread.php?p=2353114#post2353114)

---

### Post by Frickalik on 2007-03-30
If you want to Install Ubuntu/any linux distribution with Vista. use this tutorial

[http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux#Hypothesis]("http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux#Hypothesis")

i have used it myself. Works perfectly.....just dont be a noob and read it MULTIPLE times.

---

