---
title: "[SOLVED] beryl"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by mmm2010 on 2007-11-19
I just got Ubuntu (I think it's the newest version-not sure if it's feisty, edgy, whatever and I don't know how to check), but anyway, I am trying to install beryl, and I added a certain repository and key to the synaptic package manager.  I now can see all the beryl-related files, including aquamarine... libbery.... beryl....   Some of the files will download, but some won't.  I'm not sure what the problem is.  What can I do to install it?

---

### Post by DutyDuty on 2007-11-19
If you are using Gutsy, Compiz is already installed. Try running ccsm.

---

### Post by mmm2010 on 2007-11-19
I just got Ubuntu on Saturday, so I'm a COMPLETE noob.  I don't even know what Gutsy is, if I'm running it, or what you mean by "run ccsm."

When I go to Synaptic Package Manager and try to install beryl, It first tells me that a couple of other things will have to be marked as well.  After I click OK, it says the following:



Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences.

beryl:
Depends:  beryl-settings but it is not going to be installed
Depends:  beryl-manager but it is not going to be installed


Under settings>repositories, all options are checked, so I'm not sure what's wrong.

---

### Post by old_geekster on 2007-11-19
Let me be the first to welcome you to the forum and to a new experience.  There will be a learning curve at first, but it will pay dividends soon.  You can't beat the price of Linux/Ubuntu.  This is a great product.

You should open a "Terminal" (Applications/Accessories/Terminal).  In it type the following command: "cat /etc/issue" (without the quotes).  This will tell you the version of Ubuntu that you have installed; Edgy, Feisty or Gutsy Gibbon (latest version).

Ubuntu offers a new distro every 6 months.  There is also an extended version which has support for 3 years.  The next distro will be an extended one.

Here is the link to a great guide:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

This is for Gutsy, but there are guides just like it for Edgy and Feisty.  It will help you get your feet wet without some of the frustration.  The one thing that I believe is missing from the guide is an explanation of what each "Application" does for you.  You can simply do a search for the App and it will give you an explanation of its purpose.

Good luck!

One other thought.  If you are seeing "Beryl', then, you are not using Gutsy.  In Gutsy, it will be called Compiz-fusion.  The reason?  Beryl and Compiz have been brought back together as one entity; thus the fusion.  They were two separate Apps for awhile.  Compiz was the original App.

---

### Post by dhobbs on 2007-11-19
To answer your original question about Beryl.  Beryl is no longer under active development and is now known as Compiz-Fusion.  Compiz is installed by default on Ubuntu 7.10 (Gutsy Gibbon).  To enable it you should go to the System menu >> Preferences >> Appearance and click on the Visual Effects tab.  From here you can enable a minimum set of effects or a whole bunch of them.

Note: if you do not have a selection labeled "Custom" you should go to Add/Remove under the Applications menu and search for "Advanced Desktop Effects Settings" and install that program.  Make sure that it is set to Show: All Available Applications.

If you have any other questions regarding compiz you may want to look at the HOWTOs and tutorials first, then post a question here.

---

### Post by mmm2010 on 2007-11-19
The main thing that I would like is the 3D cube.  Is this the way to get that working?

(And thank you everyone for your help)

---

### Post by old_geekster on 2007-11-20
> **mmm2010 said:**
> The main thing that I would like is the 3D cube.  Is this the way to get that working?

(And thank you everyone for your help)

It would be the way to get the 3D cube if you have Gutsy.  Did you run the command that I gave you in my previous post?  This will tell you which distro you have installed.

Let us know which distro you have and we can give you more detailed instructions.

We'll have you running Ubuntu in no time at all.

---

### Post by Squizz on 2007-11-20
Try 

applications > system tools > beryl manager

It should work when you've configured it then.

---

### Post by mmm2010 on 2007-11-22
I know I haven't posted in a few days, but I did get it working.  I can't remember what all I did, but I appreciate all the help.

---

### Post by nikoPSK on 2007-11-22
lol, why Is it always solved by the time I get here (the forums are too good:p)

---

### Post by mmm2010 on 2007-11-23
Oh-by the way, I did run the command that Old_Geekster suggested, and what I got was:

Ubuntu 7.10 /n /l

Which version is this?

---

