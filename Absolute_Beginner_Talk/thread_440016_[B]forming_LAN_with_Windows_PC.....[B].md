---
title: "[B]forming LAN with Windows PC.....[/B]"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by mubed_007 on 2007-05-11
[B]Hiii Everyone...
i've been using ubuntu for some time and i just love it...
i wanted to know how to form LAN with windows PC..
i am using UBUNTU and i've 3 more pc using Windows XP...
Our pcs are LAN in windows... but i want to make LAN thru UBUNTU...
i want to use UBUNTU and others XP... my pc is server for NET and LAN...
Please help me what shud i do???
Thx in advance....!!![/B]

---

### Post by Iarwain ben-adar on 2007-05-11
First of all,
LEARN TO WAIT!

Do you really think we are all sitting here, waiting 'till someone comes along to ask questions?

Look up samba, that should do the trick ;)


Iarwain

---

### Post by starcraft.man on 2007-05-11
You'll probably want to read [this...]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server") you don't have to make ubuntu a server though, simple filesharing is possible just by turning on samba in the System > Administration > Shared Folders. Then you can share to any windows comp.

EDIT: Ya I agree with Larwain, I just noticed you posted the exact same topic not bolded 30 minutes ago, please learn a bit of patience, we aren't awake 24/7 nor do we see each and every thread >.>

---

### Post by harmeet on 2007-05-11
On 7.04 (feisty) version of Ubuntu (May work on prior versions as well) -

Goto "Places" -> "Network"
select "Windows Network".

You will see all the windows computers.

To mount a windows share from other computer (like map  an/w drive in windows) -

Goto "Places" -> "Network"
select "Connect to Server..."
under "Service type" select "Windows Share"
under "Server", write <windows computer name>/<share name>

---

### Post by esoterica on 2007-05-11
I've used Samba for years to do this, it works perfectly and it's great, it has a bit of a learning curve though so you'll need to spend some time reading and getting it set up, once you get it though it works flawlessly.

---

