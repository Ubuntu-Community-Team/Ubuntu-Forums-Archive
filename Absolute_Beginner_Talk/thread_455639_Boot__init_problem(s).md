---
title: "Boot / init problem(s)"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Cocofat on 2007-05-26
Hello there im new to forums, I currently have setup as follows

AMD AMD 5600+ cpu
DFI Lanparty UT 590 SLI 
Nvidia 5600gts SLI's
2gb ram
dual boot fiesty & visa

Have vista and ubuntu running dual boot, I played around with ubuntu in MS Virtual machine last night and it works fine. Today I decided to do a proper install and im having a few problems.

Install works ok once ACPI is disabled in the bios, I get to login screen and login, startup sound plays Ubuntu splash screen displays a grey box in the top left appears covering around 1/8th of the screen that when the mouse goes over it turns into a text type pointer and it just sits there cannot do anything at all.

the other problem is this acip, if i have it enabled (normal) it will not boot after grub comes up with an error saying I need to use no apic option, so i disable it in bios to boot but i have to enable it to load vista

can anyone supply any solutions to my woes? it would be a huge help, I have used redhat in the past but this is going back around 4-5 years so please be patient with me im willing to learn :) thanks.

---

### Post by Cocofat on 2007-05-26
actually i have managed to clear the acpi issues with adding acpi=ht the the kernal boot line but im still getting no luck after login I can access the terminal but I dont really know what im doing in there

---

### Post by jwm0z on 2007-06-04
Did you find a solution to the grey box problem?  I'm having the same problem, it seems to occur randomly and if I reboot it's fine.

---

