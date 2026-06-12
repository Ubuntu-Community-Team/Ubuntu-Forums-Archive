---
title: "zipping?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by phy5ik on 2006-12-24
how to unzip an ace?

how to .rar zip a folder?

plz help :)

---

### Post by PriceChild on 2006-12-24
*thread moved and bumped*

---

### Post by bodhi.zazen on 2006-12-24
I can never remember all that stuff.

Put this in ~/.bashrc:> # Extract files from any archive
# Usage: ex <archive_name>

ex () {
if [ -f $1 ] ; then
case $1 in
*.tar.bz2) tar xjf $1 ;;
*.tar.gz) tar xzf $1 ;;
*.bz2) bunzip2 $1 ;;
*.rar) rar x $1 ;;
*.gz) gunzip $1 ;;
*.tar) tar xf $1 ;;
*.tbz2) tar xjf $1 ;;
*.tgz) tar xzf $1 ;;
*.zip) unzip $1 ;;
*.Z) uncompress $1 ;;
*.7z) 7z x $1 ;;
*) echo "'$1' cannot be extracted via extract()" ;;
esac
else
echo "'$1' is not a valid file"
fi
}

# Thanks to rezza at Arch LinuxYou can,  of course if you prefer, with minor modification, save this as a separate script :p

Now, in a terminal type:```
source ~/.bashrc
```

Now to unzip, unarchive, what have you,

```
ex /path/to/archive_name
```

---

### Post by po0f on 2006-12-24
bodhi.zazen,

Just FYI, you can OR options that are equivalent, ie *.tar.bz2 and *.tbz2 are the same file type, so:
```
[FONT="Courier New"]# Extract files from any archive
# Usage: ex <archive_name>

ex () {
if [ -f $1 ] ; then
  case $1 in
    *.tar.bz2 | *.tbz2) tar xjf $1 ;;
    *.tar.gz | *.tgz) tar xzf $1 ;;
    *.bz2) bunzip2 $1 ;;
    *.rar) rar x $1 ;;
    *.gz) gunzip $1 ;;
    *.tar) tar xf $1 ;;
    *.zip) unzip $1 ;;
    *.Z) uncompress $1 ;;
    *.7z) 7z x $1 ;;
    *) echo "'$1' cannot be extracted via extract()" ;;
  esac
else
  echo "'$1' is not a valid file"
fi
}

# Thanks to rezza at Arch Linux[/FONT]
```

Woo hoo, saved all of two lines.  ;)

---

### Post by phy5ik on 2006-12-24
will this decompress ace files? how about re-zip folders?

---

### Post by macogw on 2006-12-24
That's for decompressing.  To zip stuff, just highlight the files you want to zip up, right click, and hit "Create Archive", on the File Roller popup, name the file, choose .rar, .zip, or whatever you want it to end in, then under that choose where you want it to go.

---

### Post by tommytom on 2006-12-27
Okay i followed the instructions above and used po0f's script to extract an .ace file, this has left me with a .swo and .swp file. How can i change these to get the original format? or have i  made a mistake somewhere?

---

