---
title: "Hardware RAID using NForce4...."
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by ZeusABJ on 2006-06-20
Now that I've got my partition scheme figured out I'd like to find the best method to "span" my two brand new Seagate 320GB drives together into one massive 640GB drive for partitioning. I have a DFI NF4 SLI-DR Motherboard, with RAID controllers built in (one Silicon Image controller and one Nvidia NForce4 RAID controller). My original plan was to try and implement hardware RAID-0 with one of those controllers. Now I'm wondering if my kernel has driver support for this sort of thing. So that brings me to my questions regarding RAID support in Ubuntu:

[LIST=1]
[*]Does anyone know if hardware RAID for either of those controllers will work in Ubuntu? 
[*]If hardware RAID is not an option is there a way to "span" two drives together so they appear as one? 
[*]Assuming the answer to question #2 is “yes”, will such spanning result in any kind of performance degradation?
[/LIST]

Thanks in advance for any advice anyone can offer!
[COLOR="Red"]
UPDATE:[/COLOR]

Here are two excellent guides for anyone else trying to implement SATA RAID in Ubuntu:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[https://help.ubuntu.com/community/In...tion/LVMOnRaid](https://help.ubuntu.com/community/In...tion/LVMOnRaid)

---

### Post by ZeusABJ on 2006-06-21
No answer huh? Well I did struggle with where to post this. I guess it sorta fall outside the realm of "beginner talk". I'll copy it over to the hardware section. Sorry if this was too tech-centric for this forum.

---

### Post by ZeusABJ on 2006-06-22
If anyone else is looking for help in this department these seem to be the definitive guides:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[https://help.ubuntu.com/community/In...tion/LVMOnRaid](https://help.ubuntu.com/community/In...tion/LVMOnRaid)

Good luck!

---

