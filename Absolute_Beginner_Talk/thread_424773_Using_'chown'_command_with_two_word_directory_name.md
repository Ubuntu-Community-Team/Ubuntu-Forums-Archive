---
title: "Using 'chown' command with two word directory name [Resolved]"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by trishacupra on 2007-04-27
Cool, it worked. What a relief.

Now, I have another partition mounted in media/Media Centre

How do I put that in the command seeing the directory has a space in it? (The space between the words Media and Centre)

---

### Post by aysiu on 2007-04-27
Type ```
sudo chown -R trisha:trisha /media/Media
``` but before hitting **Enter**, hit the **Tab** key twice.

---

### Post by trishacupra on 2007-04-27
I tried hitting Tab twice before enter, but I still got:

```
trisha@trisha-laptop:~$ sudo chown -R trisha:trisha /media/Media
chown: cannot access `/media/Media': No such file or directory
```

---

### Post by trishacupra on 2007-04-27
Oh, I've got it. I didn't put in the space after Media before hitting Tab twice.

---

### Post by trishacupra on 2007-04-27
This is what I have now...

trisha@trisha-laptop:~$  sudo chown -R trisha:trisha /media/Media 
.azureus/                     .kde/
.bash_history                 .local/
.bash_logout                  .macromedia/
.bashrc                       .mcop/
.cache/                       .mcoprc
.config/                      .metacity/
.DCOPserver_trisha-laptop__0  .mozilla/
.DCOPserver_trisha-laptop_:0  .nautilus/
Desktop/                      .openoffice.org2/
dirlist                       .profile
.dmrc                         .qt/
.esd_auth                     .recently-used
.evolution/                   .recently-used.xbel
Examples/                     .sudo_as_admin_successful
.fontconfig/                  .sword/
.gaim/                        test
.gconf/                       test~
.gconfd/                      .themes/
.gdesklets/                   .thumbnails/
.gksu.lock                    .tomboy/
.gnome/                       .tomboy.log
.gnome2/                      .Trash/
.gnome2_private/              Trish's memory verses.bvc
.gnomesword/                  .update-manager-core/
--More--

I'm guessing that's not what we wanted?

---

### Post by trishacupra on 2007-04-27
I had a separate question in my thread here: [http://ubuntuforums.org/showthread.php?t=424750](http://ubuntuforums.org/showthread.php?t=424750) that didn't relate to the subject line, so I'm posting it separately.

I want to do this command:

sudo chown -R trisha:trisha /media/Media Centre

There's a space in the directory name that's stuffing up the command. What do I do? Must I change the directory name? (Meaning I'd have to change the fstab also, unmount and remount it?)

---

### Post by aidanr on 2007-04-27
sudo chown -R trisha:trisha /media/Media\ Centre

---

### Post by bikeboy on 2007-04-27
Quotation marks should also do the trick.
sudo chown -R trisha:trisha "/media/ Media Centre"

---

### Post by aysiu on 2007-04-27
That's weird. **Tab** should fill it in: ```
username@ubuntu:~$ sudo mkdir /media/Media\ Centre
Password:
username@ubuntu:~$ cd /media/Media\ Centre/
username@ubuntu:/media/Media Centre$ cd
username@ubuntu:~$ sudo chown -R username:username /media/Media\ Centre/
Media Centre/
username@ubuntu:~$ sudo chown -R username:username /media/Media\ Centre/
``` If not, just use the backslash and space.

---

### Post by trishacupra on 2007-04-27
Thanks!

I figured out why the suggestion to hit Tab twice before Enter didn't work  - silly me got the file name wrong - 'Multimedia Centre' not 'Media Centre'. Time for a nap - too much Ubuntu for today.

---

### Post by trishacupra on 2007-04-27
Thanks!

I figured out why the suggestion to hit Tab twice before Enter didn't work - silly me got the file name wrong - 'Multimedia Centre' not 'Media Centre'. Time for a nap - too much Ubuntu for today.

---

### Post by BLTicklemonster on 2007-12-19
Um... never mind.

---

