---
title: "Sharing FIREFOX PROFILE"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by ashrack on 2005-12-04
My pimpin' profile of FF is on the WinXP partition NTFS. Now I would like to share this profile with FF in UBUNTU
Could this be possible?

---

### Post by ashrack on 2005-12-05
*bump*

---

### Post by Gray. on 2005-12-05
Well, the basic idea is to (bear in mind I may be incorrect):

Copy from C:\Documents and Settings\<windows username>\Application Data\Mozilla\Firefox\Profiles\*.default\ the following files:
bookmarks.html cert8.db cookies.txt formhistory.dat key3.db signons.txt history.dat  mimeTypes.rdf

and then place them in:

/home/<ubuntu username>/.mozilla/firefox/*.default/

making sure that they are changed to make <ubuntu username> the owner of said files.

I'm not too good with bash and scripts etc. so hopefully someone can help with that.

BTW, I got my information from [here]("https://wiki.ubuntu.com/FirefoxNewVersion") and just some general knowledge I picked up. Hopefully it helps.

**Note: backup your firefox settings as described in the link provided before attempting this**

---

### Post by jrib on 2005-12-05
I think you want to use windows sometimes and ubuntu sometimes but keep the changes you made while using the other OS.  If that's so, keep reading!  If you have a fat32 partition (you need to be able to read and write from both windows and linux) it shouldnt be too hard to do.

1. In windows copy your profile folder to your fat32 partition.
2. Create a shortcut for firefox so that it uses the copy in the fat32 partition.  Step 2 in the following link may be helpful (but there may also be another way to change the profile folder that I am unaware of): [http://www.mozilla.org/support/firefox/tips#oth_usb](http://www.mozilla.org/support/firefox/tips#oth_usb) .  Replace the paths in the link with the correct ones for your setup.  Please see the edit at the bottom of this post for some more info on this.
3.  Use the shortcut you made to run firefox and you should be set in windows.

4.  Now let's make sure firefox in ubuntu uses that same folder.
5.  You probably already know how to mount partitions, if not search the wiki for: mount windows

You have two options now.  Use the same method in windows to run firefox or create a symbolic link.

If you choose to create a symbolic link,
6.  backup your profile folder in ~/.mozilla.
7. delete the original profile folder and replace it with a symbolic link to the shared profile folder in your fat32 partition.


I haven't tried this but I think it should work.  Let me know if it works for you if you decide to use it.

[edit]  Read [http://kb.mozillazine.org/Profile_Manager#Custom_profile_location](http://kb.mozillazine.org/Profile_Manager#Custom_profile_location) about moving your profile.  It may be a better solution than step 2 above.

---

### Post by ashrack on 2005-12-05
JASON
That's exactly what I want. But I only have NTFS! So will it work with NTFS also?

---

### Post by jrib on 2005-12-05
[QUOTE=ashrack]JASON
That's exactly what I want. But I only have NTFS! So will it work with NTFS also?[/QUOTE]

Any changes you make in ubuntu will not be saved because ubuntu does not have write support for the ntfs filesystem. I don't know if there is a way to make windows access the folder (with read and write capabilities) on ubuntu's filesystem.  If there is, that would be your best option.  

Instead, you could consider creating a small fat32 partition (maybe 1GB, but if you just want the profile it could be much smaller).  That way you can use it to transfer files between ubuntu and windows as well.

---

### Post by franks1 on 2005-12-05
This link may be of some additional help,,but you still need a FAT32 partition to do the share.

[http://wiki.kanotix.net/CoMa.php?CoMa=ProfileSharingMozilla](http://wiki.kanotix.net/CoMa.php?CoMa=ProfileSharingMozilla)

Regards

FrankS

---

### Post by ashrack on 2005-12-06
Taxn
Gonna try you advices when I get home. Have 9hours of school to attend to. This is the worst school day in the week since we have so many hours.Yoy I wanna play w/ UBUNTU

---

### Post by ashrack on 2005-12-07
I only have NTFS partition. Will change Win2k partition to FAT32 when I get the spare time and also the Win2k partition is only arround 20GB so that's no problem for FAT32.
So in the meantime I copied the Windows Firefox profile into linux, and in CHROME.RDF change the path to extensions to reflect the changes and now I also have a pimpin profile in UBUNTU :)
btw. Whenever I get to change from NTFS to FAT32 I will surely check this thread again and try your advices.
Tanx 4 the help guys.

U're all great

---

### Post by raoufn1984 on 2007-07-08
> **Gray. said:**
> and then place them in:

/home/<ubuntu username>/_.mozilla/firefox/*.default/_



why i can't find this folder on my pc

---

