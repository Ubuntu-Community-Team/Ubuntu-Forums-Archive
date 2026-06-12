---
title: "Two Grub questions"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by Pattycake on 2005-12-15
I used Grub with my Breezy install and it found all my drives with no problem.  I even like that it left the loader for Windows drives.  I use this comp for work and now I'd like to arrange it so that the Windows loader is the default choice and the first thing that comes up on Grub so that I can turn on the box unattended.  How do I do that?

Also, if you don't use Grub, how do you access Breezy when the pc starts up?  Is this possible? 

Thanks

---

### Post by NotJustANewbie on 2005-12-15
You can use any bootloader for booting into different OS's on that machine, lilo for example is yet another boot loader.

[http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub) << answer to your first question.

---

### Post by canadianwriterman on 2005-12-15
EDITED TO CORRECT

Open a Terminal window and type:

sudo gedit /boot/grub/menu.list (**could be menu.lst**)
(If the text editor opens an empty file, then try sudo gedit /boot/grub/menu.lst)

This will open the menu.list file in a text editor. The file may look confusing and there will be many lines with ## in front of them. You need to look for all of the boot options. They'll look like this:

title Ubuntu, kernel 2.6.12-10-386 
root (hd0,2)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd /boot/initrd.img-2.6.12-10-386
savedefault
boot

One of the options will be for Windows. Start at the top of these boot options and count them. There should be about five options, including Ubuntu kernel boot options, memtest and Windows. It's important to note that you need to start counting at "0," not "1." So, the first boot option in the file is "0," the next is "1," etc. You'll find that Windows will be at the bottom of the list, so it should be maybe option "4" or "5."

Now, find a line near the top of the file that says "default." The standard default is usually option "0." Change the "0" to the number that represents your Windows OS.

Save the file and close it. Now, you should see Windows highlighted as the default when you boot next time. If not, just note what did get set as the default and go back in and re-edit menu-list to get the correct one.

Hope that helps!

---

### Post by az on 2005-12-15
There was a utility to change the behaviour of grub from gnome, but it was disabled because of some bugs.

You can easily tell grub to boot into windows by default, instead of ubuntu.  

You need to edit the /boot/grub/menu.list file and tell it which entry is the default.

***I have been beaten to the punch...

---

### Post by Pattycake on 2005-12-15
Thanks NotJustA..., I'll check that out.

What I meant is if I uninstall Grub is there any access to linux without a loader of any sort?  Since I share this machine it would be nice to leave it looking like a Windows machine without anyone being wise to the linux partition.  I was thinking of a key combo that would load the linux install instead of Windows?

---

### Post by Pattycake on 2005-12-15
Thanks for the quick replies all!

The step-by-step is particularly helpful.  

I'll assume a no to the second question unless anyone pops in with a suggestion.

Thanks again, this is a great site!

---

### Post by Ted D. on 2005-12-15
Hi,
Go to the following link. It should help. 
[http://ubuntuforums.org/showthread.php?t=95969&highlight=making+xp+default+grub](http://ubuntuforums.org/showthread.php?t=95969&highlight=making+xp+default+grub)
You have insert the commands and changes in grub throught the terminal window found under applications.
Ted D.

---

### Post by Herman on 2005-12-15
> I used Grub with my Breezy install and it found all my drives with no problem. I even like that it left the loader for Windows drives. I use this comp for work and now I'd like to arrange it so that the Windows loader is the default choice and the first thing that comes up on Grub so that I can turn on the box unattended. How do I do that? I agree with the information the others have already given, but would like to add that after changing the default to boot Windows, you can uncomment the line with the word 'hiddenmenu', and set the timer for a fewer number of seconds. (Like 1,2, or 3 seconds, instead of 10).
[COLOR=Red]Do not set the timer to zero whatever you do, with Windows as the default or you'll lose Ubuntu!
 [COLOR=Black]Then, when anyone else starts your computer, they won't see GRUB at all, just a black screen for a few seconds. Then it will boot into Windows if that's what you set it for.
 But when you start the computer, and you want the GRUB menu, to choose Ubuntu or any more operating systems, you just press your 'esc' key during the two or three second counting interval you set, and GRUB will show up. 

[/COLOR][/COLOR]>  Also, if you don't use Grub, how do you access Breezy when the pc starts up? Is this possible?  There are lots of ways to do that, but they are all more trouble than they are worth. You can set up NTLoader in WIndows, or use GAG bootloader from a floppy disk, but you'll still need either GRUB or Lilo to boot Ubuntu in either case, it's just more and more complicated, but you can do it. The more complicated you make things the more chances for problems though, but you can do it. I'd stick with GRUB, it's nice and simple and you'll get used to it and learn to love it very quickly! (Herman)
P.S. : find the GRUB Help page in my 'sig link' below for more details on editing GRUB's menu.lst file

---

### Post by az on 2005-12-15
[QUOTE=Herman][COLOR=Red]Do not set the timer to zero whatever you do, with Windows as the default or you'll lose Ubuntu!
 [COLOR=Black][/QUOTE]

Been threre, done that.  You still get a chance to hit escape.  That message is just not displayed on the screen.  If you hit escape just before grub runs, the keypress is stored inthe buffer (YMMV) and grub will look for it.

If not, you can always boot the install cd into rescue mode and chroot into you ubuntu install and fix it.

---

