---
title: "Ubuntu Mounting Issues!?!"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by dillbertdabomb on 2006-08-16
I just wanna see what ubuntu can do with some of my files. When I booted my computer I have my memory stick in it. It appears on my desktop and works fine. so i go to places > computer. screenshot.png shows that it sences my hard disk. than I click it screenshot1.png shows what happens. so than I go to system > administration > disks screenshot2.png shows that my drive is "active". So I click browse to get the result of screenshot3.png . Than I go to gnome partition manager to see whats there than I get screenshot4.png . Now every time I click my hard drive in Places > computer I get a message saying 

You do not have the permissions to view the contents of disks - conf - hda2

So what is wrong? hopefully the screenshots help. Yes I've sudoed it, no it doesnt work. and what does the lock icon beside the drive mean in the partition editor mean? and will it do this after install?

thanks for the help!

---

### Post by meng on 2006-08-16
The most straightforward way to solve this is to go to the command line. Did you follow my advice from your previous thread?

---

### Post by dillbertdabomb on 2006-08-16
that didn't work it when i look at the partitions from it it didn't ahow anything

its permissions!

---

### Post by meng on 2006-08-16
What exactly have you tried typing from the command line and what error did you get?

---

### Post by dillbertdabomb on 2006-08-16
it is already mounted but when i click on the drive it says you don't have the permissions to view the contents 

look at screenshots!

---

### Post by meng on 2006-08-16
I did look at them. I think the drive is NOT mounted despite your protestations to the contrary. It IS pertinent that /dev/hda2 is an NTFS partition, though, which you neglected to mention in this or the previous thread.

It seems we're having a communication problem here. Since I can't persuade you to try it my way, someone else will have to give you advice. Good luck.

---

### Post by dannyboy79 on 2006-08-16
I looked at your screenshots, you say it's mounted yet your own screenshot says pmount could not be executed. If someone is trying to help you why wouldn't you just listen to what they have to say, they are obviously trying to help you if they have bothered to take the time and answer your question! I really dislike people that ask for help but then don't try what someone suggests!!! I wish I could help you but I am a newbie. What folder is hda2 being mounted to? Is that folder owned by you? Are the permissions set to read on that folder? Those are pretty simple questions that you should answer first. Sorry I couldn't have ben more help!

---

### Post by meng on 2006-08-16
[http://www.ubuntuforums.org/showthread.php?t=237311&highlight=mount+ntfs](http://www.ubuntuforums.org/showthread.php?t=237311&highlight=mount+ntfs)
This is I think a similar problem to yours, try following this thread. If I knew more about NTFS I would have made some suggestions myself.

---

