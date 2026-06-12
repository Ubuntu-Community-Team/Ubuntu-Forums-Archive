---
title: "Can't figure out where I'm supposed to move my FFsettings"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2006-12-29
Hey folks. So I now know how to restore my settings in Firefox 2.0 from a previous version. My problem now is figuring out where to put it . . .I know I should be putting it in my .Mozilla folder, but I tried that and can't seem to get it done . . . here's what I tried:

mac@mac-desktop:~$ mv /mac/desktop/ffsettings ~/home/mac/.mozilla
mv: cannot stat `/mac/desktop/ffsettings': No such file or directory
mac@mac-desktop:~$ mv /home/mac/Desktop/ffsettings ~/home/mac/.mozilla
mv: cannot move `/home/mac/Desktop/ffsettings' to `/home/mac/home/mac/.mozilla': No such file or directory

Can you make heads or tails out of that? I can't. ~LOL~

---

### Post by bulldog on 2006-12-29
Take a look if the .mozilla exist,it should be but you'll never know.........:D

---

### Post by meng on 2006-12-29
~/.mozilla is the same as /home/mac/.mozilla

~/home/mac/.mozilla is really /home/mac/home/mac/.mozilla

See?

---

### Post by CheshireMac on 2006-12-29
> **meng said:**
> ~/.mozilla is the same as /home/mac/.mozilla

~/home/mac/.mozilla is really /home/mac/home/mac/.mozilla

See?

mac@mac-desktop:~$ mv /desktop/ffsettings ~/.mozilla
mv: cannot stat `/desktop/ffsettings': No such file or directory

I just can't win here. ~LOL~ Any thoughts?

---

### Post by meng on 2006-12-29
CM - you are going to have to pay more attention to what you're typing, perhaps take a moment to really look at your file/folder structure.

I assume this ffsettings file is on your Desktop. If so, it is located in ~/Desktop
(not /desktop and not ~/desktop)

Please try:
mv ~/Desktop/ffsettings ~/.mozilla

---

### Post by CheshireMac on 2006-12-29
> **meng said:**
> CM - you are going to have to pay more attention to what you're typing, perhaps take a moment to really look at your file/folder structure.

I assume this ffsettings file is on your Desktop. If so, it is located in ~/Desktop
(not /desktop and not ~/desktop)

Please try:
mv ~/Desktop/ffsettings ~/.mozilla

Okay, so that worked . . .should that be all I need to do, or is there a configuration I need to perform?

---

### Post by meng on 2006-12-29
Try running firefox and see what happens.

---

### Post by CheshireMac on 2006-12-29
> **meng said:**
> Try running firefox and see what happens.

~LOL~ It's what I feared. . .nothing happened. Okay . . .here's the deal: The folder called 'ffsettings' was automatically created in a backup procedure that I can't even remember how to perform. ~LOL~ It was part of the steps I took in installing the new 2.0 version. I made sure that the folder was created in Desktop, but I wasn't sure what to do with it . . .so just now, I moved it to .Mozilla . . .nothing happened. I even rebooted to see if that would do anything. Notta . . .~LOL~ Help me . . .I'm so inept. ~LOL~

---

### Post by meng on 2006-12-29
I'm not familiar with this ffsettings file and where it belongs. You may also have folders in your ~ (i.e. /home/mac !!!!!) called .mozilla-firefox and/or .firefox
Perhaps they belong there, but it's just a complete guess.

---

### Post by ThrobbingBrain66 on 2006-12-29
From reading the posts, I have a feeling that ffsettings is a backup of the .mozilla folder in the home directory. If that's the case, and to make sure it's really working, I would do this:

```

rm ~/.mozilla

```

then rename ffsettings to .mozilla (so just give it a right-click>rename)

then

```
cp ~/Desktop/.mozilla ~/
```

If you then open Firefox and have all your settings back, you can delete the folder from the desktop

EDIT:  could also be in the folders that meng listed.  open your home folder and hit ctrl+h and all of your hidden folders will show.  let us know which of the folders you have (.mozilla .mozilla-firefox .firefox)

---

### Post by CheshireMac on 2006-12-29
> **ThrobbingBrain66 said:**
> From reading the posts, I have a feeling that ffsettings is a backup of the .mozilla folder in the home directory. If that's the case, and to make sure it's really working, I would do this:

```

rm ~/.mozilla

```

then rename ffsettings to .mozilla (so just give it a right-click>rename)

then

```
cp ~/Desktop/.mozilla ~/
```

If you then open Firefox and have all your settings back, you can delete the folder from the desktop

EDIT:  could also be in the folders that meng listed.  open your home folder and hit ctrl+h and all of your hidden folders will show.  let us know which of the folders you have (.mozilla .mozilla-firefox .firefox)

Can't remove .mozilla because it's a directory apparently . . .so I can't take that step . . .and even if I did remove it, I don't have the ffsettings folder on desktop anymore because I moved it to .mozilla. Argh!! ~LOL~ This is frustrating . . .

---

### Post by ThrobbingBrain66 on 2006-12-29
Ok, yes, don't remove it now, lol.  Anyway, can you open up your home folder (/home/mac) then hit ctrl+h.  Does .mozilla show up?  .mozilla-firefox or .firefox?

---

### Post by meng on 2006-12-29
ls ~/.mozilla/ffsettings
(if it is a folder, you will get a folder listing, otherwise it will just display the single file)

If it is a folder and you want to replace .mozilla, try this:
mv ~/.mozilla/ffsettings ~
mv ~/.mozilla ~/.mozillabackup
mv ~/ffsettings ~/.mozilla

(I'm not exactly sure how mv works with folders, so if you get an error, just let us know.)

---

### Post by CheshireMac on 2006-12-29
Okay . . .I've moved the ffsettings folder back to my desktop . . .and I've found the .mozilla folder, with the firefox directory . . .so many folders . . .

---

### Post by meng on 2006-12-29
How did you get this ffsettings file/folder? Can you explain what you did to get it? Is it the same as saving your User Profile? If so then apparently it needs to be moved INTO
~/.mozilla/firefox/
[http://www.mozilla.org/support/firefox/profile](http://www.mozilla.org/support/firefox/profile)
PS Good luck, I'm bugging out at this point, I have a feeling if I keep reading this thread I'm going to go postal.

---

### Post by ThrobbingBrain66 on 2006-12-29
ok, now you can do the last two steps that meng posted above:

mv ~/.mozilla ~/.mozillabackup
mv ~/Desktop/ffsettings ~/.mozilla

---

### Post by CheshireMac on 2006-12-29
I have a thought . . .I've found identically named files in one of the sub-directories in firefox . . .if I were to replace them with the backedup versions of themselves, would that restore everything?

---

### Post by ThrobbingBrain66 on 2006-12-29
> **CheshireMac said:**
> I have a thought . . .I've found identically named files in one of the sub-directories in firefox . . .if I were to replace them with the backedup versions of themselves, would that restore everything?

I think I follow what you're saying, it SHOULD work.  And, if it doesn't as long as you still have your settings on your desktop, you can't hurt anything.
[COLOR="Red"]
EDIT:[/COLOR] It seems you've used this HOWTO to install firefox: [https://help.ubuntu.com/community/FirefoxNewVersion?highlight=%28newversion%29](https://help.ubuntu.com/community/FirefoxNewVersion?highlight=%28newversion%29)
 The relevant info you need to restore your settings is here (from the howto):

Restore your old data:

 cd ~/Desktop/ffsettings
 mv * ~/.mozilla/firefox/*.default

---

### Post by CheshireMac on 2006-12-29
> **ThrobbingBrain66 said:**
> I think I follow what you're saying, it SHOULD work.  And, if it doesn't as long as you still have your settings on your desktop, you can't hurt anything.
[COLOR="Red"]
EDIT:[/COLOR] It seems you've used this HOWTO to install firefox: [https://help.ubuntu.com/community/FirefoxNewVersion?highlight=%28newversion%29](https://help.ubuntu.com/community/FirefoxNewVersion?highlight=%28newversion%29)
 The relevant info you need to restore your settings is here (from the howto):

Restore your old data:

 cd ~/Desktop/ffsettings
 mv * ~/.mozilla/firefox/*.default

No change. This is really confusing, especially for something that should be intensely simple . . .~LOL~ I don't get it . . .my computer is a mess, too . . .I think so anyhow. I need to be better organized.

---

