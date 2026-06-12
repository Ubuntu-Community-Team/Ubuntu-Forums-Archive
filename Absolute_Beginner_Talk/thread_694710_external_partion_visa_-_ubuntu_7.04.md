---
title: "external partion visa - ubuntu 7.04"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by trigsenior on 2008-02-12
hello ,

I have an external hard drive 465 GB , im using vista which works fine apart from its in french and can not change it to english so it makes life much harder for me  :(  This is why i want to boot ubuntu and vista .

I was using this totorial [http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/#more-253"]the totorial /#more-253](http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/#more-253"]the totorial /#more-253)
it was fine but im unsure on what they mean by -
IMPORTANT: Ensure that all internal hard drives are disconnected from your computer during the install (pull your SATA or IDE cables)

what are SATA or IDE cables and do i need to do it ?

and also will i need to partion my external hard drive or do i have to loss all my files ?

thanxs and am looking forward do your humble opinions   :)


ps : and in you opinons which would be better for a ubuntu nub (like my self 7.04 OR 7.10 ?) ?

---

### Post by smartboyathome on 2008-02-12
I would recommend [this guide](http://ubuntuforums.org/showthread.php?t=678146) over that one. It tells you how to fix it so that you don't need to remove the other hard drives from your computer.

---

### Post by rkd on 2008-02-12
IDE cables or SATA cables are the wires that connect the hard drive to the computer's motherboard. The reason the instructions tell you to disconnect them is so that there is no chance that installing Ubuntu will change anything on your Windows disk.

I hesitate to try to describe them, because, especially for IDE cables, it is a little tricky to handle them without bending pins in the connector or putting them in backwards when you reconnect them. I think it would be a better idea for you to find someone close enough to you who can come and show you how to handle them. There is a good chance that there is a Linux User's Group somewhere near you. They usually have people eager to help folks get started with Linux. If you tell us what city you are in, we probably can find a nearby group (there are directories of them on the web).

If you want to plunge on yourself, these cables come out of the back of your hard drive. There also are power cables coming out of the back of the hard drive. It is fine to disconnect both. Be sure you make note of the orientation of the cables so you can reconnect them exactly as they were. If your disk is an IDE disk, the connector is very wide with many pins -- be very careful when unplugging and reconnecting that you don't bend any of the pins in the connector.

If you have a notebook computer, you would have to remove the hard drive instead of disconnecting cables, and that is hard to do on some models -- look for the owner's manual for your computer.

Contrary to what smartboyathome said, I think it is better to take the approach of disconnecting the existing hard drive(s) so that you have no risk of accidently wiping out their contents. If you try to follow the instructions smarboyathome pointed to, if you slip up, you could accidently lose data on your hard drives. It comes down to how cautious you want to be. An advantage to the directions smartboyathome points to is that you don't have to fiddle with cables.

---

