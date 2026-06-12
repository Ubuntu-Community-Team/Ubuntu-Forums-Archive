---
title: "Total Linux Newb"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by illumined21 on 2007-02-02
I,m trying to boot ubuntu off a live cd and am having no luck at all. It starts up fine, but once it gets to the loading screen it just goes back and forth for a bit then locks up on a black screen...no errors or anything. Im a complete noob when it comes to linux...so any help would be much appreciated.

AMD FX-53
2g DDR
74g WD Raptor in raid
X850 ATI
Windows XP currently installed

---

### Post by loserboy on 2007-02-02
yay for linux noobs :)  

what version are u trying to install 6.06 (dapper) or 6.10 (edgy)

---

### Post by illumined21 on 2007-02-02
trying 6.10

---

### Post by loserboy on 2007-02-02
[https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)

follow the steps on the 1st one under installation (thats what fixed mine), but if thats not it also check the other ones, there should be something there for you.

alternatively dapper almost always works for everyone, so maybe try the dapper livecd just to test it.

---

### Post by illumined21 on 2007-02-02
Awesome, ill give that a shot. Thanks!

---

### Post by deadgobby on 2007-02-02
Often when installing Ubuntu i386 on an AMD64 board you will have to hit F6 and enter the following paramaters

irqpoll pci=noacpi noapic nolapic acpi=off

to get The Ubuntu i386 Alternate or LiveCD to Boot correctly. 

Gobby

---

### Post by illumined21 on 2007-02-02
great, i will try that as well...do i hit F6 while it is loading?

---

### Post by loserboy on 2007-02-02
when you get to the boot screen where it asks if you want to boot/install or safe mode, hit F6 then at the bottom a line of text will show up and you add those parameters.

(correct me if i'm wrong deadgobby)

---

### Post by deadgobby on 2007-02-02
You are correct....:)

---

