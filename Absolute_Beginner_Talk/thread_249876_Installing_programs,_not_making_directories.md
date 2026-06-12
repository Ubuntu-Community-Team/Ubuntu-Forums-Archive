---
title: "Installing programs, not making directories"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Osirls on 2006-09-03
Ok i am  trying to install drivers for my ATI Radeon x850 pro, but when i run the proprietry setup tool everything seems to go fine, but when it comes to me trying to run the autoconfig --intial from the directory things should've been extracted to, the directory or any of the files do not exist!

I am running commands from terminal using sudo to get root access, is there anything else i'm doing wrong?
I don't get any error messages when running the commands, only file not found when i try to run the autoconfig..

This also happens when i tried to install a Silicon image driver.

I ran 'sudo tar xvzf JAVA_RAID_GUI.tgz' which completed successfully.
Then tried to execute 
'sh "usr/local/SiI/SiICfg/Start_RAID_GUI.sh"'
but it cannot find the files because the files didn't aren't there!

What am i doing wrong?!
I can't install anything until i find out..

Thanks,
Osiris

---

### Post by jorn on 2006-09-03
Maybe your fogot to change to the directory where the files are located.
When they are on the Desktop then type:
> cd /home/your_username/Desktop
and go on from there.

---

### Post by Osirls on 2006-09-03
I wish that were so but as you can see with the command 'sh "usr/local/SiI/SiICfg/Start_RAID_GUI.sh"' it actually points the the correct directory so it should work.

On the otherhand i can't enter the directory because it simply doesn't exist! I've looked in Nautilus and it's none of the fils are there.

---

