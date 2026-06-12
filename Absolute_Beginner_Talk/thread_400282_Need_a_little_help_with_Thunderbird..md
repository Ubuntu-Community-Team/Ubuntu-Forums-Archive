---
title: "Need a little help with Thunderbird."
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by bosstweed on 2007-04-03
Hello all! Just installed Edgy last night- let me first say that these forums are beyond impressive! Seems like an amazing community. Here's my question:

I had Thunderbird on my Windows XP, and I saved the necessary folders to an external drive so that I could recover the emails I had saved in the program. Where do I go to insert these folders (if possible) so that they will once again be stored in Thunderbird? 

Thanks much!

---

### Post by qprfact on 2007-04-03
Are you running dual boot or just Ubuntu? If the former, you can share the mail files between both operating systems!

[http://learn.clemsonlinux.org/wiki/Email:Sharing_your_Thunderbird_profile](http://learn.clemsonlinux.org/wiki/Email:Sharing_your_Thunderbird_profile)

---

### Post by kellemes on 2007-04-03
from terminal...

<run> thunderbird -profilemanager

from dialogbox..
Delete current profile..
Create new profile, and point it to the profile you have saved from windows.
Finished!

---

### Post by flossgeek on 2007-04-03
What I do is go to my home folder press "Ctrl + h" to show hidden files. Look for the .mozilla-thunderbird folder and in there are your profiles, add your old profile, you can delete the other profile that may have been created when you first launched Thunderbird. Easy ;-).

---

### Post by bosstweed on 2007-04-03
Thanks for all the help! I used flossgeek's suggestion since I'm quite the noob! :lolflag:

---

### Post by tchoklat on 2007-05-03
> **kellemes said:**
> from terminal...

<run> thunderbird -profilemanager

from dialogbox..
Delete current profile..
Create new profile, and point it to the profile you have saved from windows.
Finished!


I did this though when I start Thunderbird it asks me to setup email accounts etc. What am I doing wrong?

This is my profiles.ini file:

[General]
StartWithLastProfile=1

[Profile0]
Name=tony
IsRelative=1
Path=1nwb6joly.default
Default=1

---

### Post by tchoklat on 2007-05-03
bump

---

### Post by alienexplorers on 2007-05-03
Sounds like Thunderbird is not pointing to the correct profile directory.  Run thunderbird -profilemanager and delete current profile.  Create a new profile and the copy your profile data into the new profile that you made.  Try starting thunderbird and see what happens.

---

### Post by ubnewbie2 on 2007-05-03
You can even just dump the files from your old profile into the new one that Thunderbird creates on a new install. When you start Thunderbird, all your old setup and emails are magically there.

---

### Post by tchoklat on 2007-05-03
that is what I did and it doesn't work. It always attempts to create new addresses, etc. I copy the old profile to the new and it does not read it. I must be doing something simple. I had no problem with Firefox.

I have deleted all profiles. Restarted and of course a profile is created. I copy all old addresses, mail etc into the hi7re8f.default profile and it STILL 'sees' nothing and asks me to set Thunderbird up again.

---

### Post by octoberdan on 2007-05-03
> **tchoklat said:**
> that is what I did and it doesn't work. It always attempts to create new addresses, etc. I copy the old profile to the new and it does not read it. I must be doing something simple. I had no problem with Firefox.

I have deleted all profiles. Restarted and of course a profile is created. I copy all old addresses, mail etc into the hi7re8f.default profile and it STILL 'sees' nothing and asks me to set Thunderbird up again.

If you saved the entire profile directory of your last installation, delete hi7re8f.default and drop in your old profile?

---

### Post by ubnewbie2 on 2007-05-03
> **tchoklat said:**
> that is what I did and it doesn't work. It always attempts to create new addresses, etc. I copy the old profile to the new and it does not read it. I must be doing something simple. I had no problem with Firefox.

I have deleted all profiles. Restarted and of course a profile is created. I copy all old addresses, mail etc into the hi7re8f.default profile and it STILL 'sees' nothing and asks me to set Thunderbird up again.

You did stop Thunderbird while you copied the data, then started it again afterwards didn't you?

I just copied all the data under the obscurely named profile directly, and it worked.

---

### Post by tchoklat on 2007-05-03
Yep, done it again. I deleted the .Thunderbird directory, started Thunderbird which created a new directory with a defaullt profile. I then closed thunderbird and copied the entire contents of my old profile 2141gf14.default directory into the one created by Thunderbird, I checked that the profile.ini was pointing to the correct profile (Which it was) and started Thunderbird up.

The same, it asks me to set up the mail addresses etc.

For what it is worth, my profiles.ini file is;

General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=0mcckgvt.default

which points to the correct profile directory

I noticed when Thunderbird starts it creates a lock file in the profile and deletes it when I close the program. Is this significant?? It also creates a .parentlock file and this is not deleted when the program is closed. Am I clutching at straws? Why is it not working? What am I missing!

help!!!!

---

### Post by ubnewbie2 on 2007-05-03
Straw clutching, yeah, me too.  Don't know how much more I can offer.  What about the version of Thunderbird? I am using 1.5.0.10 that came with feisty.

---

### Post by tchoklat on 2007-05-03
Yahoo I fixed it.  

Appears that the problem may be in the version of Thunderbird (Great call ubnewbie2). I used a back up version of settings, emails etc and all went well. I then copied one by one directories over to the profile making sure it was working. As I had copied the files off a CD I had to amend Write permissions but all is OK.

This is a bug I s'pose. 

I now have an up to date address book, emails and account settings.

great!

---

### Post by rcmullins on 2007-05-04
Yes, so far I'm not at all impressed with 'MozillaZine's attempt at helping navigate or update/change thunderbird up.  They seem to be more interested in giving Windows users help.  They have the file structure wrong, there is no chrome folder when you install t-bird, there is no userChrome.css there is not user.js.

I want to view my email in html form, but all I can seem to get is this plain-jane text based stuff.  I don't care if it is less secure or not, I think I should be  the one to decide that.  If not I'll go back to Microshi*.

Just sort of ranting here, btw, evolution has got to be the ugliest UI I have ever seen on a email application.

Anybody have any good reference sites for hacking t-bird on Linux so I can get html-encoded messages?

(Sorry if I offended anyone with the Evolution statement.)

---

### Post by ubnewbie2 on 2007-05-04
No html?  Mine has ALWAYS been able to show html mail.

---

### Post by rcmullins on 2007-05-04
When my t-bird was running on XP it showed html mail.  But now it gets stripped of all the html formatting.

To try and discover what was wrong with it mozilla-zine said I needed to edit the chrome (which I am familiar with in FF).  So I navigated to my ~.mozilla-thunderbird/profile folder and no chrome, no CSS (which is what is supposed to allow me to see html encoding) and no user.js (which mozillazine assured me would be there.)

They even got the file structure wrong.  MZ said that your thunderbird profile is in the ~.mozilla folder, but it isn't.  Firefox is in there, but not thunderbird.  The profiles for thunderbird are kept in ~.mozilla-thunderbird.

So for what its worth........

Incidentally I tried just creating the css by hand to see if tbird would pick it up and use it, but it did not work.

---

