---
title: "Little backup file cleaning script/service"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2008-01-03
I made this little script as more of a service to run in the background and search periodically (every 3 minutes) for files ending in ~ (backup files for text documents).  Granted, the first run will be a little slow, but once it's scanned once, subsequent scans should only take a fraction of a second (I have upwards of 50GiB of data and subsequent scans only take about that long ;)).

```

#!/bin/bash
while [ 1 == 1 ]; do
[COLOR=Sienna]sleep 180
files=$(find "$HOME" -name "*~");[/COLOR]
[COLOR=DarkRed]if [ "$files" != "" ]; then[/COLOR]
[COLOR=DarkOliveGreen]zenity  --notification  --window-icon="/usr/share/icons/Human/24x24/actions/gtk-about.png"  --text "Useless files detected!"[/COLOR]
[COLOR=DarkSlateBlue]files=$(find "$HOME" -name "*~");
zenity --question --text "remove them?\n$files"[/COLOR]
[COLOR=Blue]    if [ "$?" -eq "0" ]; then
    find "$HOME" -name "*~" -print0|xargs -0 /bin/rm -f[/COLOR]
[COLOR=Purple]else
    sleep 1
    fi
else
sleep 1
fi[/COLOR]
[COLOR=SeaGreen]auto-clean &
exit 0[/COLOR]
done

```I'm assuming only people who can read this and get it will use it (saving me the need to put warnings, etc. ;))
But the basic gist of it is...
1. [COLOR=Sienna]every 3 minutes it will scan your home for useless text files[/COLOR]
2. [COLOR=DarkRed]if some are found[/COLOR], [COLOR=DarkOliveGreen]a little "i" in a bubble will appear in the notification area[/COLOR] - *nothing else* that gets in your way or interrupts.
3. [COLOR=DarkSlateBlue]if you click it, a dialog will appear with a list of what should be removed (after a quick re-scan to be sure that's what it's doing)[/COLOR]
[COLOR=Blue][COLOR=black]4. [/COLOR]you can then click OK to remove the files,[/COLOR] [COLOR=Purple]or cancel to sleep for 2 seconds and then continue the 3 minute sleep then search loop.[/COLOR]

Note 1 - if you want the script to pause and remain dormant, simply don't click the "i" bubble.

Note 2 - [COLOR=SeaGreen]you'll notice that every 3 minutes (after everything is done) the script will start a second copy of itself and then quit, leaving you with just 1 copy again, but this is in case you've changed the code - the new code will now be running (assuming the script is in your $PATH and is called "auto-clean"). You can remove this feature be just deleting these lines.
[/COLOR]

---

### Post by ryanVickers on 2008-01-03
What? NO one's gonna comment on how this is a stupid waste of resources or how its the most brilliant thing ever?? :p

---

### Post by Xavieran on 2008-01-09
My friend this *is* the most brilliant thing I have ever seen...
Seriously,Thanks...:):):):KS:):):)

---

### Post by Gwasanaethau on 2008-01-09
Yeah, I have to agree, it certainly looks good! However, I sometimes need those little '*~' gems for the times I mash up my scripts/markups! But I can certainly see where it would be useful, and I for one would use it if I was more careful with saving stuff! :lol:

Good work! :guitar:

---

### Post by Xavieran on 2008-01-09
When I run it it gives me this:
```
xavieran@Le-Chateau:~/Code/scripts$ sh cleanup.sh 
[: 19: ==: unexpected operator

```

Any idea what's wrong?

Nevermind...I changed the == to = and now it works..thanks...

---

### Post by ryanVickers on 2008-01-09
wow I'm surprised people like this... :D

and it should have just worked as is...

---

