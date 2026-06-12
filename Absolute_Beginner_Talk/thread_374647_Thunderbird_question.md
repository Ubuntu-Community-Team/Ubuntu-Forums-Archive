---
title: "Thunderbird question"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Jimmy4eyes on 2007-03-02
I'm not sure if this is the correct board but I am an absolute begginer. I installed Thunderbird because of the familiarity of using the windows version. I would like to have all my emails that are in the windows version, available on my Ubuntu machine, but keep all the same header information. Is there a way to do this?

---

### Post by PartisanEntity on 2007-03-02
What exactly do you mean with "keep all the same header information" ?

---

### Post by Jimmy4eyes on 2007-03-02
Sorry, I'm probably not saying this right.. I have shedloads of emails in Thunderbird on my windows laptop, going back a couple of years. I'd like these on my Ubuntu desktop as well, but still showing as the same dates of delivery etc.

I had thought just to forward them to a webmail account then set Ubuntu Thunderbird to download them all but apart from that taking ages, they would all show up with the same, new date.

They're all from my main gmail account, with copies left on the server. I've looked to see if I can just download them all from there into my desktop but I can only see how to get new ones.

---

### Post by PartisanEntity on 2007-03-02
Okay now I understand. I believe it is possible to set up Thunderbird to access gmail. If that is the case, you could do a test run by selecting to keep the original emails on the gmail server, once the emails have been downloaded you could check the headers to see if they have been messed up, but I don't see why this should happen.

You will find many threads dealing with this issue, just type "thunderbird gmail" in the search.

Usually migrating to various email clients should not be a problem, I migrated about 4000 emails dating back to 2002 from MS Outlook, to Thunderbird and then to Evolution, none of the header information ever changed.

---

### Post by aysiu on 2007-03-02
Just copy this folder:

C:\Documents and Settings\jimmy\Application Data\Thunderbird

to this folder (if you're using Ubuntu's Thunderbird):

/home/jimmy/.mozilla-thunderbird

or this folder (if you're using Mozilla's Thunderbird):

/home/jimmy/.thunderbird

---

### Post by DJ_Peng on 2007-03-03
Simply copying from one folder to another actually won't work since you're moving from one OS to another with a different file structure. You can also check the Mozillazine Knowledge Base article [Moving your profile folder](http://kb.mozillazine.org/Moving_your_profile_folder).

---

### Post by aysiu on 2007-03-03
> **DJ_Peng said:**
> Simply copying from one folder to another actually won't work since you're moving from one OS to another with a different file structure. Uh, I've done it before, and it's worked. I've also advised people to do it, and they've said it works. You can try to logic it out all you want. Experience tells me differently.

---

### Post by DJ_Peng on 2007-03-03
My experience is that it didn't work, but i guess my milage varied. It's cool. Thanks for the correction.

---

### Post by aysiu on 2007-03-03
> **DJ_Peng said:**
> My experience is that it didn't work, but i guess my milage varied. It's cool. Thanks for the correction.
No, apparently, you're right. There's one other step you have to do, because one file refers to an absolute (not relative) path:
[Copy Thunderbird settings from Windows to Linux](http://ubuntuforums.org/showpost.php?p=2186159&postcount=3)
[HOWTO: Copy your Thunderbird email and settings from Windows XP to Ubuntu.](http://ubuntuforums.org/showthread.php?t=45950)

---

### Post by DJ_Peng on 2007-03-03
That's why it didn't work for me. Although please allow me to provide links to Mozilla's instructions. I realize Ubuntu users have been through it a lot of times, Mozilla's instructions may provide steps developed as users left Windows to more OS'es than just ours.

[Moving your profile folder]("http://kb.mozillazine.org/Moving_your_profile_folder")
[Migrating settings to a new profile]("http://kb.mozillazine.org/Migrating_settings_to_a_new_profile")

---

