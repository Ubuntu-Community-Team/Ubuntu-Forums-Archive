---
title: "Attention Beginner Team:  The Documentation Team needs your help!"
date: 2008-06-09
forum: Beginner Team
---

### Post by CloudFX on 2008-06-09
Hello Beginners Team!

The documentation team is working on putting together troubleshooting sections for each of the major categories in the official documentation that can be found on help.ubuntu.com or System > Help and Support.  As there are so many possible support issues that may come up, we are looking at you guys to help provide us with the most common ones that come up here on the forums.  Some examples are the 'X won't start' issue, or 'dpkg --configure -a'.

Have a look at the [blueprint]("https://blueprints.edge.launchpad.net/ubuntu-doc/+spec/troubleshooting-guide") and the [spec]("https://wiki.ubuntu.com/TroubleshootingGuide") for more information.

How you can help:
First of all, I'd like to mention that *everybody* can contribute.  You don't have to be a member of the Beginner's team, and the more suggests we get, the better.



If you would like to help out, please put together a text file of the support issue and best answer, categorized in the following groups:

[LIST]
[*] Adding and Removing Software
[*] Files, Folders, and Documents
[*] Desktop Customization/Graphical Problems
[*] Internet/Connectivity
[*] Music, Video, and Photos
[*] Printing and Faxing
[/LIST]

**For example:**
Question:  I tried to run Synaptic, and received a *dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.*
Solution:  Open a terminal (Applications > Accessories > Terminal), and enter *sudo dpkg --configure -a*.

Submit this file in this thread, or email me directly.  Full credit will be given towards you and the Beginner's team!

---

### Post by cprofitt on 2008-06-09
When running the nvidia restricted driver I was unable to setup twinview.

The solution was to force the refresh of the second LCD.

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: 1280x1024_60 +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Rocket2DMn on 2008-06-09
For further information about working on the Community Wiki, see the Wiki Focus Group's page - [https://help.ubuntu.com/community/Beginners/Team/FocusGroups/Wiki](https://help.ubuntu.com/community/Beginners/Team/FocusGroups/Wiki)
Our plan of attack is still being developed, but there are a lot of useful links there in sections 3 and 4.  Feel free to contact me if you have questions regarding getting involved with the Wiki FG and/or Community Docs via the ubuntu doc team.

---

### Post by spiderbatdad on 2008-06-09
Would like to see something in the way of informing potential users about boot parameters...for those who frequently post: "I can't get Ubuntu to boot from the live CD." OR "Ubuntu take 5 min. to start."

The F6 option is there, but no newcomers seem to notice it...or what to do with it. If they find their way to the F6 F3 screen...they still wouldn't know how to apply the potential parameters like: noapic nolapic....

I have tried my hand at a blog here...but I know it needs works.

[http://spiderbatdad.wordpress.com/ubuntu-boot-problems/](http://spiderbatdad.wordpress.com/ubuntu-boot-problems/)

OK. made my first wiki: [https://help.ubuntu.com/community/BootParameters?action=show](https://help.ubuntu.com/community/BootParameters?action=show)

---

### Post by bodhi.zazen on 2008-06-09
I started a faq here :

[https://help.ubuntu.com/community/Beginners/FAQ](https://help.ubuntu.com/community/Beginners/FAQ)

See section 1

[list=number][*]Feel free to modify the FAQ (Add / remove).
[*]Will start with current content
[list][*]Wiki
[*]forums threads
[*]3rd party links[/list]
[*]Please identify areas of the wiki needing content or updates.[/list]

---

### Post by Rocket2DMn on 2008-07-09
You can follow some of the major progress here - [uhelp]community/Beginners/Development[/uhelp]
Don't think that covers everything :)

---

