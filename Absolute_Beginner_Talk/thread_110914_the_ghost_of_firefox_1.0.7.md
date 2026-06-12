---
title: "the ghost of firefox 1.0.7"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-01-01
i followed the instructions on this page [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) to upgrade from version 1.0.7 to 1.5 of firefox. unfortuantely, it appears that 1.0.7 is still on my computer. it will occasionally pop up instead of 1.5, especially if i select 'web browser' from the menu of an alternative window manager. so, how do i get rid of it? i've looked through the files and it appears that 1.5 might be identified as 'firefox' while 1.0.7 is identified as 'mozilla-firefox'. when i enter 'mozilla-firefox' in the command line, it opens 1.0.7, but i don't want to just start deleting everything called 'mozilla-firefox'. (entering 'firefox' opens 1.5.)

---

### Post by audax321 on 2006-01-01
Well according to those directions 1.0.7 is still installed because it is required for certain ubuntu packages. What that how-to does is install a second version of Firefox and symlink the bin file for it to /usr/bin/firefox.

The other bin at /usr/bin/mozilla-firefox is still pointing to the old version so try the following:

```

backup the mozilla-firefox file: cp /usr/bin/mozilla-firefox /home/<username>
link 1.5 to mozilla-firefox: sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

```

If you don't encounter any problems you can probably go ahead and delete the backed up file from your home folder. If you want to go back to the old way where mozilla-firefox opens 1.0.7, then:

```

restore mozilla-firefox file: sudo cp /home/<username>/mozilla-firefox /usr/bin/mozilla-firefox

```

---

### Post by fuscia on 2006-01-01
when i did this - *sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox* - i got a message saying that the file already exists. i remember doing - *sudo ln -s /opt/firefox/firefox /usr/bin/firefox* - as part of the upgrade process. the original problem still exists. did i leave something out? thanks for the response, btw.

---

### Post by audax321 on 2006-01-01
Well the how-to had you do this:

```

 sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/firefox

```

I'm guessing that first line renamed /usr/bin/firefox to /usr/bin/firefox.ubuntu and  told apt to use that instead of /usr/bin/firefox... that is why you never got the file already exists error when you made that link. So I guess just try the same thing with mozilla-firefox:

```

 sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

```

Other than that I have no other ideas.... good luck. :)

---

### Post by kenweill on 2006-01-01
[QUOTE=fuscia]i followed the instructions on this page [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) to upgrade from version 1.0.7 to 1.5 of firefox. unfortuantely, it appears that 1.0.7 is still on my computer. it will occasionally pop up instead of 1.5, especially if i select 'web browser' from the menu of an alternative window manager. so, how do i get rid of it? i've looked through the files and it appears that 1.5 might be identified as 'firefox' while 1.0.7 is identified as 'mozilla-firefox'. when i enter 'mozilla-firefox' in the command line, it opens 1.0.7, but i don't want to just start deleting everything called 'mozilla-firefox'. (entering 'firefox' opens 1.5.)[/QUOTE]

To ensure that other programs use version 1.5 of firefox and not the old 1.0.7 version, go to Preferences -> Preferred Applications in the System menu. For the "Web Browser" tab, choose "Custom" and then enter the command:

firefox %s

Try it. It works for me. Solved my problem.

---

### Post by fuscia on 2006-01-01
[QUOTE=audax321]Well the how-to had you do this:

```

 sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/firefox

```

I'm guessing that first line renamed /usr/bin/firefox to /usr/bin/firefox.ubuntu and  told apt to use that instead of /usr/bin/firefox... that is why you never got the file already exists error when you made that link. So I guess just try the same thing with mozilla-firefox:

```

 sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

```

Other than that I have no other ideas.... good luck. :)[/QUOTE]

that seems to have done it. thanks for the help.

---

### Post by fuscia on 2006-01-01
[QUOTE=kenweill]To ensure that other programs use version 1.5 of firefox and not the old 1.0.7 version, go to Preferences -> Preferred Applications in the System menu. For the "Web Browser" tab, choose "Custom" and then enter the command:

firefox %s

Try it. It works for me. Solved my problem.[/QUOTE]

the problem is i'm using openbox which uses a very plain preference menu. thanks for the answer, though.

---

