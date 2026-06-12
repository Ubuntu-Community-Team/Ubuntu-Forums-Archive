---
title: "Importing mail in Thunderbird"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by theexbrit on 2006-10-29
Hi all, :-k  I know I can import my address book from my Windows XP Thunderbird into my Ubuntu Thunderbird, but how can I get all my old messages & folders imported?

TIA. ](*,)

---

### Post by rccharles on 2006-10-29
> **theexbrit said:**
> Hi all, :-k  I know I can import my address book from my Windows XP Thunderbird into my Ubuntu Thunderbird, but how can I get all my old messages & folders imported?

TIA. ](*,)


Here is a hint.

Maybe you could install Netscape 7.1 on XP and  convert the mail to Netscape format.  ( Netscape 7.1 has a built in mail reader. ) With this format, you loaded the mail into Thunderbird.

Robert

---

### Post by yabbadabbadont on 2006-10-30
Try copying the contents of the "Mail" directory from your WinXP Thunderbird's profile directory to the "Mail" directory in your Linux Thunderbird's profile directory.

It may not work as text files are stored with different line ends in Dos/Win than in Linux.  As a work around, if you don't have a *huge* amount of mail, you could forward it all to yourself.

---

### Post by dmizer on 2006-10-30
yeah ... there's no need to convert anything.  everything converted directly from my windows box over to my ubuntu with no problems in the translation.  i just copied the mail folder in the thunderbird profile.

in fact, if you copy your whole profile folder, all your mail settings will be transfered (not just your inbox messages).  in some cases, this even includes your extensions.

---

### Post by theexbrit on 2006-10-30
For the life of me, I can't figure out where the Thunderbird folder is on the hard drive!! ](*,) Where do all the program folders reside?:confused: 

:-k

---

### Post by yabbadabbadont on 2006-10-30
Are you asking where your profile is for the Windows version or the Linux version?

In Linux, there will be (once you have run the program at least once) a hidden directory in your home directory called .mozilla-thunderbird

I don't remember where it is in Windows.

---

### Post by theexbrit on 2006-10-31
I've copied the "Thunderbird" folder from the Windows box & put it on the desktop of the Ubuntu box. Now I just need to figure out how to get it copied to the folder in Ubuntu that holds the mail, etc.

Edit:
I just searched for a "profile" folder in Ubuntu & it didn't find any folder called profile.

---

### Post by theexbrit on 2006-10-31
It's really strange, I've found several articles on the web regarding copying Thunderbird profiles, but where they say my profile, Thunderbird file, etc, should be, they aren't there!

I found some Thunderbird folders in "/share" & "/usr", but none seem to have a profile or address book file, etc.

---

### Post by theexbrit on 2006-10-31
In Linux, there will be (once you have run the program at least once) a hidden directory in your home directory called .mozilla-thunderbird

You mention a "hidden" file. Do I have to change preferences or something to access this file?

---

### Post by the_priest on 2006-10-31
In your windows box you'll find your current profile under:
"C:\Documents and Settings\*username*\Application Data\Mozilla\Thunderbird"

or

"C:\Documents and Settings\*username*\Local Settings\Application Data\Mozilla\Thunderbird"

Sorry not sure which of the too coz i don't have it installed atm.

As for the hidden file, in the standard gnome browser you'll need to "show hidden files" in one of the drop down menus.

---

### Post by cotcot on 2006-10-31
[http://www.mozilla.org/support/thunderbird/profile]("http://www.mozilla.org/support/thunderbird/profile")

Look under > Move an existing profile or restore a backed up profile

---

### Post by theexbrit on 2006-10-31
Yeah, I read that article but there is no "/.mozilla-thunderbird" directory in the Ubuntu system as far as I can see.

---

### Post by dmizer on 2006-10-31
you can't see it because it's a hidden file.

in nautilus, select view > show hidden files.  or in the terminal, just
```
cd /home/theexbrit/.mozilla-thunderbird
```

---

### Post by theexbrit on 2006-10-31
Ok, got it! Found the directory & copied the profile over. Now when I start Thunderbird it tells me Thunderbird's already running & to restart the computer. 

After restart I get the same message again when I start T/bird.

Edit::::

Ok, I did it! I was trying to import the whole profile & it was messing everything up (changing IsRelatives, etc), so I just copied all the contents of the XP profile into the Ubuntu profile instead of the whole profile folder & it works great. It just takes some getting used to the Ubuntu file system after using XP for all this time. But I'm getting the hang of it. 

Thanks for all your help everyone.

---

