---
title: "Erasing Hardrive"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by sneffers on 2007-04-20
Hi, I just burned Feisty to a cd and works in a desktop I have but not in the laptop. I am a complete begginner. I found stuff about partitions on [this]("http://www.psychocats.net/ubuntu/separatehome") page, But I don't know if I can erase my hardrive with that because I want to erase my hardrive, "cause I believe that Might make the cd work.

---

### Post by spin2cool on 2007-04-20
Your question isn't very clear, but I'm guessing that you want to erase everything on your hard drive, repartition it, and then install Ubuntu, right?  This will cause you to lose all the data on your hard drive, so make sure this is what you want to do.

If so, boot from the live CD, and run the installer.  Be sure to choose the option a few steps in that will let you partition your hard drive yourself.  When the partitioner comes up, delete all of the existing partitions, and create 3 new ones.

1) about 15 gigs, formatted ext3 - you will mount '/' here

2) 1gb, formatted linux-swap - you will mount 'swap'  here

3) all the rest formatted ext3 - you'll store your data here.  (you may choose to mount your /home partition here or just leave it as a seperate data partition)

4) Proceed with the install.

---

### Post by sneffers on 2007-04-20
It's not so much as repartitioning, But erasing the hardrive. My edgy cd works perfectly fine, but my feisty doesn't work. Edy crashd on me so all it has is the loading image and then an error so i figured if I wipe it then it will be able to read the feisty cd.

---

