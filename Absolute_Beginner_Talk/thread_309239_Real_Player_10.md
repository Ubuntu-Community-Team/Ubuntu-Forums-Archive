---
title: "Real Player 10"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2006-11-29
i am using ubuntuguide.org, and i downloaded the bin file, now its asking me for a patch where it will install the software, tell me where should i install it...

---

### Post by taurus on 2006-11-29
Either in your $HOME directory or you can install it in /opt/RealPlayer!!!

---

### Post by compmodder26 on 2006-11-29
Have you tried using Automatix?

---

### Post by wpshooter on 2006-11-29
I think you mean **path** to install it.

I just did this recently and I believe that it will display by default the path at which you downloaded the .bin file.

I installed mine to **/home/download/realplayer **and it worked fine.  BUT let me warn you that to make sure that you use the **SUDO** command to both chmod +x on the downloaded file and also when you run the installer, otherwise it will not work properly.

Good luck.

---

### Post by shoaibi on 2006-11-29
hmmmm wpshooter youyr are like i wanna know a path where i should install it like in windows C:\Program files\, i don't wanna install everything in my home directory, so where should i install it?

---

### Post by wpshooter on 2006-11-29
I believe the actual place it should be installed is in a /usr directory but I am not really familar with where various type of software installations are supposed to be installed.

Maybe someone else can give you the preferred path.

---

### Post by Ben Sprinkle on 2006-11-29
/opt/realplayer

/opt Is where most big software is installed. :)
Then to run you would type for example:
```

sudo ./opt/realplayer/bin/real

```
If it gives some crap about non-executable type:
```

sudo chmod 777 /opt/realplayer/bin/real
```
Have fun. :)
I see your asking alot of questions which is good, keep asking!

---

### Post by shoaibi on 2006-11-29
Hmmm waiting for other *GOOD* people like wpshooter ;)

---

### Post by Ben Sprinkle on 2006-11-29
Or you can install in /usr so all you have to type is:
```

sudo real

```

But it's just a fashion to install in /opt :)

EDIT:

Or or, you can install in /opt/realplayer and make a link to the binary file in /real into /usr/bin so you can still type real and it will work:
```

sudo ln -s /opt/realplayer/real /usr/bin

```
I think that's the command. (Havn't used in awhile, might be wrong.)

---

### Post by shoaibi on 2006-11-29
Goat Spirit:
using this:
sudo ./opt/realplayer/bin/real
gives:
sudo: ./opt/realplayer/bin/real: command not found

---

### Post by Ben Sprinkle on 2006-11-29
My bad, no . , .'s are for current directory like:
```

sudo ./real

```
So if you install in /opt/realplayer/ then type:
```

sudo /opt/realplayer/bin/real

```
There. :)

---

### Post by shoaibi on 2006-11-29
and by the way what's this thing about which RealPlayer asks me about:
configure system-wide symbolic links? [Y/n]: ...
???
What if i say Y, then what should i give on next screen?

[Now don't stop me, i will ask and ask ;) ]
[Sorry i know i am being quite lazy, but please let it be for the first time :(]

---

### Post by Fully216 on 2006-11-29
try 'locate real' to see where the executable is located.

Edit: sorry, didn't see other posts

---

### Post by Ben Sprinkle on 2006-11-29
Type yes shoabi.

---

### Post by shoaibi on 2006-11-29
hmmm goat spirit i typed yes and now it asks:
enter the prefix for symbolic links [/usr]: 

what next?

---

### Post by Ben Sprinkle on 2006-11-29
Type @

---

### Post by shoaibi on 2006-11-29
Thanks a lot everyone. Installed,
Problem Solved.

---

### Post by Ben Sprinkle on 2006-11-29
Good good, I hate real lol. Brother is obsessed with it in windows, drives me mad. :)

---

### Post by shoaibi on 2006-11-29
i am also driven mad, but i thought what if some files refuse to play in totem or VLC, so just as a backup, nothing else.

---

