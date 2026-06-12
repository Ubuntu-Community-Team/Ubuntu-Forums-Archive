---
title: "Trouble with my triple boot (Lion, Ubuntu 12.04, Win7) Win 7 won't boot"
date: 2012-05-19
forum: Apple Hardware Users
---

### Post by Antyks on 2012-05-19
So I went through this tutorial online to help me triple boot my MBP. I already had Win7 and Lion partitioned on it using BootCamp. I used refit and everything seemed to go smoothly. Lion boots perfectly and so does Ubuntu but not so much Windows. Every time I click on the windows button in the refit menu it takes me to Ubuntu and bring me to a screen with a list of drives. I see Windows 7 loader, so I click that. This takes me to a black screen with a white cursor blinking in the top left. This seemed normal to me because this is what Windows looked liked before when I tried booting it but the problem is that it never loads, it just stays on that black screen. I have also tried holding "option" down at start up and clicking the windows partition but it does the same thing. Please, please help! I would appreciate anything. Thanks!

tutorial: 
[http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)

---

### Post by coffeecat on 2012-05-20
*Thread moved to **Apple Users**.*

@Antyks, you mistakenly posted to the Tutorials and Tips forum and your post was stuck in the moderation queue. I've moved it to the Apple forum where someone may be able to help you.

---

### Post by Hanger84 on 2012-05-20
I'm not sure what kind of Mac your using, or if your using a Hackintosh, but I know that Lion causes issues with its recovery partition. The best way to get around that, is to boot from a Lion disk and use Disk Manager to partition the drive however you want it divided (ex: 3 equal partitions, 3 partitions and a swap partition, etc.) So that Lion doesn't make the recovery partition.

Other than that, I got 20.04 to work just fine on my MacBook Pro 2011 by installing OSX Snow Leopard, Then Windows 7, and then using a 12.04 Alternate x64 CD to install. In the options during install, I selected to install Grub to my MBR.

Hope that helps you or someone else that might have issues installing Ubuntu on a MacBook Pro 2011.

---

