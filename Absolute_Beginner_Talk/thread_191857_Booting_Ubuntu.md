---
title: "Booting Ubuntu"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by Drezard on 2006-06-08
I have lately downloaded and attempted to install ubuntu linux. I have done it before with an older version but, I have attempted to install the latest one but it just wont boot. I have windows xp installed on a seperate partition. I have burnt the ISO onto 2 different kinds of Cd and onto a DVD, none work. I have just named the Cd what ever the date is. Am i naming the cd wrong? What am i doing wrong? I have set up the Bios also to boot from Cd First. 

- Cheers, Daniel

---

### Post by nalmeth on 2006-06-08
You may have a corrupted image. Also I don't think you can burn the CD iso's on to a DVD? OR I might be wrong. Anyway, here is a good guide you can use to check the integrity of the image, and it shows a whole lot more. More than you probably need. 

[http://www.psychocats.net/ubuntu/windowstoubuntu.html]("http://www.psychocats.net/ubuntu/windowstoubuntu.html")

---

### Post by Fafnir on 2006-06-08
Two possible other solutions, but I think the most likely is a corrupted image.

1. You should be burning the .iso as an image - there'll probably be a specific option to that effect in the CD burner you use. You don't want to burn it as a file, or extract the files from the .iso and burn those. If you look at the CD from windows, you should see multiple files.

2. I know the CD drive is set to boot first, but it's *possible* (though unlikely) that your BIOS is ignoring you for some reason (maybe it doesn't like the CD drive). You might want to verify that it is actually booting CDs by checking it will boot from your Windows install CD or something else that you know should work.

---

### Post by underdog on 2006-06-08
An easy way to verify your image is an MD5 Checker.

[http://www.brandonstaggs.com/filecheckmd5.html](http://www.brandonstaggs.com/filecheckmd5.html)

There is a free one. The ubuntu download sites have the MD5 sums listed.

---

