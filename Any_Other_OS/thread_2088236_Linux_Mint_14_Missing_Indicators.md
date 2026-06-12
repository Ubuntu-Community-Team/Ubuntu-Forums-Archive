---
title: "Linux Mint 14 Missing Indicators"
date: 2012-11-25
forum: Any Other OS
---

### Post by Giant Speck on 2012-11-25
I upgraded to Linux Mint 14 this morning and noticed that a few of the application indicators that I previously had installed are missing.  When adding Indicator Applet Complete to the MATE Panel, the only indicators that show up are the network and sound indicators.  The session, messages, and clock indicators are missing.

Now normally, I fix this by installing indicator-datetime-gtk2, indicator-session-gtk2, and indicator-messages-gtk2, but all of these packages seem to have been dropped in the Quantal Universe repository.

Is there an alternative source -- preferably a PPA -- from which I can download and install these needed packages, or should I just try to manually install them?

---

### Post by Giant Speck on 2012-12-08
I managed to solve this by finding all of the required packages on the [Linux Packages Search]("http://pkgs.org/search/?keyword=indicator") website.  It's a bit of a sloppy method, as it involves downloading and installing several DEBs.  I don't know have the know-how, time, or patience to set up and maintain a repository, so if you are just as desperate as I was to get this working again, you can use this method.

[COLOR=DarkRed]**[CLICK HERE TO DOWNLOAD ALL OF THE REQUIRED PACKAGES]("https://www.dropbox.com/s/xw1iax1umy86o2y/Indicator-required-packages.tar.gz") (TAR.GZ / DROPBOX)**[/COLOR]

[COLOR=Sienna]**HIERARCHY OF DEPENDENCIES**[/COLOR]

[SIZE=1]**indicator-messages-gtk2 **(=0.6.0)[/SIZE][INDENT][SIZE=1]*&#8627;  depends ***indicator-messages** (=0.6.0)
[/SIZE][INDENT][SIZE=1]*&#8627;  depends*** libindicator-messages-status-provider1** (>=0.4.92)
[/SIZE] [/INDENT][/INDENT][SIZE=1]**indicator-session-gtk2** (=0.3.96)[/SIZE][INDENT][SIZE=1]*&#8627;  depends ***indicator-session **(=0.3.96)[/SIZE] [/INDENT][SIZE=1]**indicator-datetime-gtk2** (=0.3.94)[/SIZE][INDENT][SIZE=1]*&#8627;  depends*** indicator-datetime** (=0.3.94)[/SIZE][INDENT][SIZE=1]*&#8627;  depends*** libecal-1.2-10** (>=3.2.3)[/SIZE][INDENT][SIZE=1]*&#8627;  depends ***libedataserver-1.2-15 **(=3.2.3)
[/SIZE] [/INDENT][SIZE=1]*&#8627;  depends ***libedataserverui-3.0-1** (>=3.2.3)[/SIZE][INDENT][SIZE=1]*&#8627;  depends ***libcamel-1.2-33** (>=3.4)

[/SIZE][SIZE=1]*&#8627;  depends*** libebook-1.2-13** (>=3.4.4)[/SIZE][INDENT][SIZE=1]*&#8627;  depends*** libedataserver-1.2-16 **(>=3.4.4)
[/SIZE] [/INDENT][SIZE=1]*&#8627;  depends*** libecal-1.2-11** (>=3.4.4)[/SIZE]
[/INDENT][/INDENT][/INDENT][B][COLOR=Sienna]INSTALLING THE MESSAGES INDICATOR
[/COLOR][/B][COLOR=Sienna]
[COLOR=Black]Install the packages in the following order:  **libindicator-messages-status-provider1 **[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black]**&#8680; indicator-messages **[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black]**[COLOR=Sienna][COLOR=Black][B]&#8680; **[/COLOR][/COLOR]indicator-messages-gtk2[/B][/COLOR]
[/COLOR][B]
[COLOR=Sienna]INSTALLING THE SESSIONS INDICATOR[/COLOR]

[/B]Install the packages in the following order:  **indicator-session **[COLOR=Sienna][COLOR=Black]**&#8680; indicator-session-gtk2**[/COLOR][/COLOR]
[B]
[COLOR=Sienna]INSTALLING THE DATETIME INDICATOR[/COLOR]

[/B]Install the packages in the following order:  **libedataserver-1.2-16 **[COLOR=Sienna][COLOR=Black]**&#8680; libebook-1.2-13 **[/COLOR][/COLOR]
[COLOR=Sienna][COLOR=Black]**&#8680; libecal-1.2-11 **[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black]**&#8680; libcamel-1.2-33 **[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black]**&#8680; libedataserverui-3.0-1 **[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black]**&#8680; libedataserver-1.2-15 **[/COLOR][/COLOR]
[COLOR=Sienna][COLOR=Black]**&#8680; libecal-1.2-10 **[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black]**&#8680; indicator-datetime **[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black]**&#8680; indicator-datetime-gtk2**.

Once all the required packages are installed, kill mate-panel.  When it restarts, all of the indicators should be visible.

[/COLOR][/COLOR]EDIT:  Don't forget to lock the versions for indicator-session, indicator-datetime, and indicator-messages.

---

