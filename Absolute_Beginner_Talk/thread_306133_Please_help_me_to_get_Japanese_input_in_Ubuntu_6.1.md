---
title: "Please help me to get Japanese input in Ubuntu 6.10 working using UIM or SCIM."
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by lukeelliot on 2006-11-24
I have been trying all night to get Japanese input to work in Ubuntu 6.10.  I am new to Linux and Ubuntu.  To the best of my knowledge I have followed all of the steps described [here]("https://help.ubuntu.com/community/JapaneseInput?highlight=%28input%29%7C%28Japanese%29").  With the exception, that is, of entering
im-switch -s uim_anthy
into the terminal.  I tried, but I got this:
Error: no configuration file "uim_anthy" exists.
Error: No action taken.
I definitely installed all of the uim (and scim) programs mentioned.  One step I may have messed up: 
"Note: you need to have the UniversePackages repository configured."
I didn't really understand this, but I clicked on "repositories" in Synaptic Package Manager and since the "universal" box was ticked, I figured there was nothing else for me to do.  What is meant by "configure?"  Although I installed uim-applet-gnome in Synaptic and rebooted, I can't seem to find the applet in the "add to panel" window and neither uim or scim are working at all.  In fact, I can't find any indication at all that uim has really been installed except for the fact that all the uim boxes in Synaptic have green fill and check marks.  If anyone could help, I would greatly appreciate it.  I have a one week translation and interpretation course coming up and I'd really like to be able to type Japanese in Ubuntu.

---

### Post by ryukent on 2006-12-14
After you've enabled Japanese in 'Language Support', you are probably trying to use the SCIM in an English login. To make that work try opening the console and typing:


```
sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup
```

That should enable the Anthy SCIM mode in English too.

---

### Post by lanchongzi on 2007-02-13
uim is better than scim since it doesnt disturb your skype (if you have it installed )

---

### Post by ryukent on 2007-02-13
SCIM works perfectly well with Skype, you just have to set it up properly!

Also, you might want to set up the fonts properly, so Japanese doesn't look so ugly. Follow my other post:

[http://ubuntuforums.org/showthread.php?t=338991](http://ubuntuforums.org/showthread.php?t=338991)

---

