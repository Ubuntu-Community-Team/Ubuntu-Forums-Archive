---
title: "Read only"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Clay85 on 2006-05-09
I'm trying to import my Mozilla Firefox bookmarks.html file from my USB Portable Firefox, but bookmarks.html in system/etc/mozilla-firefox/profile says the file does not belong to me, so I cannot change it. Is there anyway to un-read-only a file?

---

### Post by cgjones on 2006-05-09
Your bookmarks should go in
```

/home/*username*/.mozilla/firefox/*weirdstuff*/profile/

```
or something like that. As for setting file permissions, try the following:
```

sudo chmod u+w bookmarks.html

```

I'm not familiar with Portable Firefox though, so this might not help.

---

### Post by Omnios on 2006-05-09
Couple ways of doing it export the file to your home direcotry or copy it there and owner should me changed to your user. RIght click and properties will allow you to change permitions.

 Oppsies beet me to it.

---

### Post by Clay85 on 2006-05-09
[QUOTE=cgjones]Your bookmarks should go in
```

/home/*username*/.mozilla/firefox/*weirdstuff*/profile/

```
[/QUOTE]

I don't have a home/username folder. The only folder in Home is /Desktop.

[QUOTE=cgjones]
or something like that. As for setting file permissions, try the following:
```

sudo chmod u+w bookmarks.html

```

I'm not familiar with Portable Firefox though, so this might not help.[/QUOTE]

Hmmm. I just installed Ubuntu yesterday, so I'm not quite sure what that is.

---

### Post by Clay85 on 2006-05-09
[QUOTE=Omnios]Couple ways of doing it export the file to your home direcotry or copy it there and owner should me changed to your user. RIght click and properties will allow you to change permitions.

 Oppsies beet me to it.[/QUOTE]

Is there an export button? I don't see it. :( I just right clicked it, though. I must be missing something.

---

### Post by Omnios on 2006-05-09
chmod is a terminal command to mod access modes, permitions. 
chmod --help
```
tom@reboot:~$ chmod --help
Usage: chmod [OPTION]... MODE[,MODE]... FILE...
  or:  chmod [OPTION]... OCTAL-MODE FILE...
  or:  chmod [OPTION]... --reference=RFILE FILE...
Change the mode of each FILE to MODE.

  -c, --changes           like verbose but report only when a change is made
      --no-preserve-root  do not treat `/' specially (the default)
      --preserve-root     fail to operate recursively on `/'
  -f, --silent, --quiet   suppress most error messages
  -v, --verbose           output a diagnostic for every file processed
      --reference=RFILE   use RFILE's mode instead of MODE values
  -R, --recursive         change files and directories recursively
      --help     display this help and exit
      --version  output version information and exit

Each MODE is one or more of the letters ugoa, one of the symbols +-= and
one or more of the letters rwxXstugo.

Report bugs to <bug-coreutils@gnu.org>.

```

 ```
sudo chmod u+w bookmarks.html
```
sudo does it in root, chmod u+w adds user write permitions to bookmarks.html

---

### Post by cgjones on 2006-05-09
Your user's Home directory is /home/*username*/
So your Desktop directory would be /home/*username*/Desktop/

Don't worry about the second thing I posted right now, I wasn't sure how familiar you were with Ubuntu.

Can you give me a step by step account of what you've done so far?

---

### Post by Omnios on 2006-05-09
In firefox, Bookmarks / Manage bookmarks / THen File and export.

---

### Post by Clay85 on 2006-05-09
..oh boy. What have I gotten myself into.

umm. Let me fiddle around with this for a little bit longer. x.x

Thanks for your help. o.O

---

### Post by cgjones on 2006-05-09
Just take it one step at a time. You'll figure things out. And us forumites will be here to help.

---

### Post by Clay85 on 2006-05-09
This community seems like they'll tolerate my idiocy :) I've really been trying to look stuff up, but it's hard to find what I'm looking for when I get lost three sentences into most of the literature.

Where is the command line? I looked in Applications, Places, and System. But I'm not sure what I'm looking for.

Is there somewhere that explains some very very very very simple command lines I can play with?

---

### Post by Clay85 on 2006-05-09
[QUOTE=Omnios]RIght click and properties will allow you to change permitions. [/QUOTE]

At the bottom of the properties window it says, "You are not the owner, so you can't change these permissions."

---

### Post by Omnios on 2006-05-09
Sorry command line also seems to cover the terminal lol which allows you to do command line commands lol. Anyways GO  Menu / aplications / Accessories / Termianl. Then when you open termional you can type in stuff. As for some basic command line stuff there is a link in my signature called Know your terminal commands.

---

### Post by Clay85 on 2006-05-09
Thanks. My brain is swimming. I think I'll take a break, lol. Food is good.

---

### Post by Omnios on 2006-05-09
FOr command like there are a few ways, One is to book up in recovery mode  that takes you directly to the command line. The main way to get into command line is ctl-alt F1. Then Ctl-alt F7 to go back to to GUI. Also some stuff requires you to shut down GDM but I would have to look that one up.

---

