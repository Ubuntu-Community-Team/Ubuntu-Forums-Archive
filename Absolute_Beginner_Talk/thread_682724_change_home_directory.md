---
title: "change home directory"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2008-01-30
OK I certainly dont get this. Here is what I just did:
In the terminal I changed the file /etc/passwd as root. Now what I was after was to change my home directory to ........./Desktop. OK i did it and I log in and what has happened is that there is now a folder named Desktop in my home directory with nothing in it? As a bonus I get that all my settings are back to original. I fixed it ( just change it back to what it was, the home directory I mean). Can anyone explain why this happens? I mean I don't get why should the settings be reset?

---

### Post by mikeyphi on 2008-01-30
> **KOTAPAKA said:**
> OK I certainly dont get this. Here is what I just did:
In the terminal I changed the file /etc/passwd as root. Now what I was after was to change my home directory to ........./Desktop. OK i did it and I log in and what has happened is that there is now a folder named Desktop in my home directory with nothing in it? As a bonus I get that all my settings are back to original. I fixed it ( just change it back to what it was, the home directory I mean). Can anyone explain why this happens? I mean I don't get why should the settings be reset?

File structure.... first / then Home - then User -then  Desktop, Documents etc

---

### Post by nick_h on 2008-01-30
> Now what I was after was to change my home directory to ........./Desktop.

Why do you want to do this?  Do you want nautilus to use your home folder as the desktop?

If so you just need to run gconf-editor (use Alt-F2) and set /apps/nautilus/preferences/desktop_is_home_dir

---

### Post by emarkd on 2008-01-30
All of your settings got reset because they're stored in hidden config files in your home directory.  When you changed your home directory nothing could find it's config file anymore and reset to the default.  Doing this is not recommended.

---

