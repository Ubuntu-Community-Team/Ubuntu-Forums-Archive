---
title: "Boot CD"
date: 2005-07-19
forum: Absolute Beginner Talk
---

### Post by Sve on 2005-07-19
Hi there,
I am not sure whether I am posting this in the correct forum but I figured since I am absolute beginner this might be the place. I appologize if it isn't.
My case - I have the Ubuntu sent to me and I am trying to install it over a Windows system. I have set my PC to boot from the CD but it says it can't find "a boot record" and refuses to boot in order to start installation.
Any suggestions?

Thanks in advance!

---

### Post by poofyhairguy on 2005-07-19
[QUOTE=Sve]Hi there,
I am not sure whether I am posting this in the correct forum but I figured since I am absolute beginner this might be the place. I appologize if it isn't.
My case - I have the Ubuntu sent to me and I am trying to install it over a Windows system. I have set my PC to boot from the CD but it says it can't find "a boot record" and refuses to boot in order to start installation.
Any suggestions?

Thanks in advance![/QUOTE]

Correct place to post. Welcome.

What CD are you using? The Live CD or the Isntall CD?

---

### Post by Sve on 2005-07-19
Hi!
Thanks for the welcome!
I am using the install CD... My system is with AMD processor and I was running the intel disc - do you think this matters? I mean I know for AMD64 you have to use another installation - my processor isn't 64 - it is just ordinary AMD...

---

### Post by codejunkie on 2005-07-19
[QUOTE=Sve]Hi!
Thanks for the welcome!
I am using the install CD... My system is with AMD processor and I was running the intel disc - do you think this matters? I mean I know for AMD64 you have to use another installation - my processor isn't 64 - it is just ordinary AMD...[/QUOTE]
thats the right cd to use how  did you burn the .iso file?
Edit: i saw where you said you had it sent to you sorry, did you get the cd from shipit or did someone just burn an .iso for you?

---

### Post by Lord Illidan on 2005-07-19
Did you set the burner to burn a cd from an image file (the iso) or you just dragged and dropped the iso to the cd?

---

### Post by Sve on 2005-07-19
I have the CD sent to my by shipit - it is original CD...

---

### Post by codejunkie on 2005-07-19
you might want to try the cd in a friends pc or if you have another one try it in that just to see if the cd is damaged, bad discs can happen even with pressed Cd's I've bought games & software that were bad swapped them for a new disc and it worked perfectly.
also are you sure your pc is set to boot from cd it never hurts to double check. also in the bios make sure the boot order is set like this 
```

cd-rom
floppy
hd0 /your hard drive

```
on some motherboards if anything is listed above the cd-rom drive in the boot order like the floppy or hd drive it wont boot even if boot from cd is enabled hope this helps.

---

### Post by Lord Illidan on 2005-07-19
or if you have 2 cdroms..i.e. a cd-r and a cd-rom, you might want to check both of them..I can boot from my DVD-ROM and my DVD-R...

---

### Post by Sve on 2005-07-20
[QUOTE=codejunkie]you might want to try the cd in a friends pc or if you have another one try it in that just to see if the cd is damaged, bad discs can happen even with pressed Cd's I've bought games & software that were bad swapped them for a new disc and it worked perfectly.
also are you sure your pc is set to boot from cd it never hurts to double check. also in the bios make sure the boot order is set like this 
```

cd-rom
floppy
hd0 /your hard drive

```
on some motherboards if anything is listed above the cd-rom drive in the boot order like the floppy or hd drive it wont boot even if boot from cd is enabled hope this helps.[/QUOTE]
 The booting sequence is correct - it boots from CD, then floppy and then HDD. The problem is that it doesn't recognise the CD as a bootable for some reason. I will try on another PC and with another CD as well... But it is just strange...
Cheers guys,
Sve

---

### Post by codejunkie on 2005-07-20
[QUOTE=Sve]The booting sequence is correct - it boots from CD, then floppy and then HDD. The problem is that it doesn't recognise the CD as a bootable for some reason. I will try on another PC and with another CD as well... But it is just strange...
Cheers guys,
Sve[/QUOTE]
hope you get it going good luck.

---

