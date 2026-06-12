---
title: "Thunderbird looses myprofile ach time"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by yoramdavid on 2007-09-02
Hello,

I managed to make Thunderird to use the plugins installed in windows xp and to have access to all my mail by copying the folder to Ubuntu, including the profile.
I can therefore access my contacts and all my mails from either OS but get the mails downloaded twice in (Once in each OS), which I am not too concerned about.
What bothers me is every time I run Thunderbird, it asks me to choose a user profile and the box is empty, I have to create one every time.
If I try to use the profile in my NTFS partition, it says the profile is in use and do not allow me to use it. I have to each time choose the one from the folder I created.

Thank you for your help.

Yoram David

---

### Post by thelocust on 2007-09-02
Sound like your profiles.ini file got messed up. I attached mine, try replacing it in ~/.thunderbird/Profiles.ini and then open it up and change the last line Path= to the name of the folder in /.thunderbird. If you have more than one folder then you have more than one profile. If thats the case try one at a time see which one is the one you use and delete the other.

---

### Post by thelocust on 2007-09-02
Sorry for some reason it won't let me upload the file so it is pasted below.


[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=ikf6rlfc.default

---

### Post by Grimgoil on 2007-09-02
Actually it might be a bug, in ternimal type: **Sudo nautilus** 
and enter your password
go to you home folder and switch to see hidden files, look around for the thunderbird folder, it might be in the .mozilla i don't fully recall, you need to delete it, once deleted reopen thunderbird.

the problem occurs when sometimes the folders in home (which save the individual program settings) get locked and cant be accessed  unless they know you are the super user, just need to delete them (though if you have important info in there you might need to back up the content) or maybe you can unlock it via folder options, i'm not sure, try!

---

### Post by yoramdavid on 2007-09-06
Hi thelocust and Grimgoil  ,

Thanks for the replies. After I changed the profiles.in in the thunderbird folder recently placed ther by me (home/yo/thunderbird)i, and rebooted into Ubuntu, therre was an error saying something like "It looks like your profile is in home/yo, but the file does not exist" ir then asked if I wanted to login as a different user, or with some recourses switched off but I was not able to login anymore.
I tried to replace the profile.ini from windows but it did not help.

Is it related to the profiles.ini I changed in the Thunderbird folder?
How I get around this? I am new and cannot do anything in the command lilne mode...

Thanks,

Yoram

---

### Post by alienexplorers on 2007-09-06
Create a new profile for thunderbird using the command run in terminal:
> thunderbird -profilemanager

you can then transfer data from your old profile to the new profile.  Follow these instructions:
> [http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Thunderbird](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Thunderbird)

You then can delete your old profile and hopefully your problem will be solved.

---

### Post by alienexplorers on 2007-09-06
If the above commands do not work you can create a shortcut to thunderbird and in the command section put:
Example- Yours may be different!!!!
> thunderbird  -P "profile_name"

---

### Post by thelocust on 2007-09-06
Double check that Path=(the exact name of the folder) also the Name=(might not be default)

---

### Post by yoramdavid on 2007-09-06
Thanks for the replies, but to be able to create a new profile in thunderbird, I need to be able to boot into ubunut first...

Yoram

---

### Post by thelocust on 2007-09-06
Sorry missed that part can you boot up in Recovery Mode?

---

### Post by yoramdavid on 2007-09-07
Hello,

Yes I can reboot in recovery mode, but I do not know how to use command lines.
If I make a new profile for Thunderbird this is going to solve the booting into Ubuntu problem? Whay are they related?

Thank you.

Yoram

---

### Post by yoramdavid on 2007-10-24
(Have been away for a month). Well, when I try to boot in one of the other versions of Ubuntu, I get a screen resolution problem (which I had to fix already), but do not know how to fix here, so no I cannot boot in recovery mode. Probably could in command lines, but as an absolute beginner, I do not know how to do that either.

Thanks for your help.

YoramDavid

---

