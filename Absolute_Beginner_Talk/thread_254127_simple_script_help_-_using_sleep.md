---
title: "simple script help - using sleep"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Episteme on 2006-09-09
I'm trying to learn bash scripting by building a simple script for watching tv.

Simply, it captures video to a temp.mpg file, waits for it to start saving, then opens it in mplayer.

```
#!/bin/bash

#start debug mode
set -x

#capture video output from the tuner to a temporary file
echo "saving temp file"
cat /dev/video0 > /mnt/hdb1_storage/tv/tmp/temp.mpg

#wait for 5 seconds to give the tuner time to start saving the temp file
echo "waiting 5 seconds before playing"
sleep 5

#play the output file in mplayer
echo "playing file"
/usr/bin/mplayer /mnt/hdb1_storage/tv/tmp/temp.mpg

#end debug mode
set +x
```

Unfortunately, it seems as thougth the sleep command is also putting cat to sleep too, and results in mplayer being unable to find the temp.mpg file (not enough time to create it first).

Your thoughts?

Peace,

Sean

---

### Post by kidders on 2006-09-09
It's actually **cat** that's putting **sleep** to sleep, in a manner of speaking. The **sleep** command will probably never get executed, because **cat** most likely blocks indefinitely.

What you probably want to do is push the **cat** operation into the background ... add an ampersand to the end of that line.

---

### Post by kidders on 2006-09-09
If you're insufferably particular about scriptwriting (like I am!) then you'll probably be irritated by the fact that, when your script terminates, the **cat** process will carry on beavering away in the background, until you kill it manually.

There are various ways of cleaning that end of things up, if you'd like to ... post back :-)

---

### Post by Episteme on 2006-09-09
Hi Kidders,

Many thanks for your offer of help.

Well, here's what happens when i run my script from a term window.

```
sean@pantheon:~$ /mnt/hdb1_storage/tv/script/tv.sh
+ echo 'saving temp file'
saving temp file
+ cat /dev/video0
```

After waiting for some time, I hit CTRL +C to end the script, then
```

sean@pantheon:~$ killall cat
cat: no process killed
sean@pantheon:~$ ls -s /mnt/hdb1_storage/tv/tmp/
total 14232
14232 temp.mpg
sean@pantheon:~$ rm /mnt/hdb1_storage/tv/tmp/temp.mpg
```

So, I tried it with the & at the end of that line like you suggested, and it worked perfectly!!!  THANKS!!!! 

Looks like you and I are thinking along the same lines (insufferably particular... yep, and stubborn as the day is long too) 

killall cat and rm temp.mpg are other things I would like to add for sure... eventually I want to simplify ivtv-tune -c # -d /dev/video0; use 'at' and crontab to record when I'm away, and finally learn how to encorporate zenity for a nice 'gui' for the whole thing... but wanted to start with just learning how to bring up the tv in a way that would allow me to pause it.  This works - and I'm excited about that.

so, how would you make it so that it automatically killall cat when exiting?  I'm only guessing killall cat - but what command should I use I tell the script to wait until I end mplayer? I can 'man' that command once I know what it is.

Many, many thanks!! My first script is up and running thanks to you!

Sean

---

### Post by kidders on 2006-09-09
Oh darn it! I wrote you out a nice script and the server locked up again and started timing out. ](*,) I'll write it again for you in a little while :-P

---

### Post by kidders on 2006-09-09
Hi there,

Just in case I forget, **killall cat** is a really bad idea ... anything that happened to be called that would commit suicide! If you happened to be root when you did it, all sorts of things might start dropping like flies.

Anyhow, here's one possibility. It's coming straight off the top of my head, so you'll have to forgive any typos, etc. that might be in it!!

```

#!/bin/bash

# Some variables to tweak
TEMP_NAME="/mnt/hdb1_storage/tv/tmp/temp"
VIDEO_DEV="/dev/video0"
VIDEO_PLAYER="/usr/bin/mplayer"

# Find a free filename
i="1"
while [ -e "$TEMP_NAME$i.mpg" ]
do
	i=$[$i+1]
done
VIDEO_NAME="$TEMP_NAME$i.mpg"

# Capture video in background
cat $VIDEO_DEV > "$VIDEO_NAME" &
CHILD_PID=$!

# Wait 5 seconds
sleep 5

# Is the video still buffering?
if [ -z `pgrep -P $$` ]
	then echo "Oh hell... something went all pear-shaped :("; exit 1;
fi

# Play the video
$VIDEO_PLAYER "$VIDEO_NAME"

# We're back - Clean up now!
kill $CHILD_PID
wait

# How much 'cleaning' should we do?
if [ "$1" != "-k" ] 
	then rm -f "$VIDEO_NAME"
	else echo "What you've just seen is at $VIDEO_NAME"
fi

```

Now, this is pretty long-winded, so let me explain:

[LIST=1]
[*]**Some variables to tweak** - No harm in putting some stuff at the top, for easily tweaking the specifics of how a script works.
[*]**Find a free filename** - There's no point accidentally overwriting something! This loop will help call your movies temp1.mpg, temp2.mpg...
[*]**Capture video in background** - We're interested in the PID of the process we spawn here.
[*]**Wait 5 seconds** - Well... obvious :-)
[*]**Is the video still buffering?** - Maybe the "cat" process died for some reason ... we might as well check, before mplayer starts.
[*]**Play the video** - Obvious, except that I'm assuming mplayer will block here until it terminates.
[*]**We're back - Clean up now!** - Specifically kill the "cat" process.
[*]**How much 'cleaning' should we do?** - I've invented a "k" (keep) switch to let you stop your movie from vanishing.
[/LIST]

I hope this is a bit closer to what you're after. Call it something like **/usr/local/bin/pausable_tv**. Then, say you wanted to prevent the script from trashing your buffered movie, invoke it with:

```

pausable_tv -k

```

---

### Post by kidders on 2006-09-09
One thing worth mentioning is that, while these kinds of scripts can be very handy, they do present a security issue. You should maybe consider prepending your script with something like the following, and doing **sudo chown root:root /usr/local/bin/pausable_tv && chmod 755 /usr/local/bin/pausable_tv**.

```

if [ "$UID" = "0" ]
   then echo "Tut tut, you should know better than that!"; exit 1;
fi

```

This would discourage your from running it as root. If you *were* to run this script as the super-user, imagine the impact of the malicious addition of **rm -Rf / 2> /dev/null** on the end! Equally, of course, it limits the possible damage caused by a scripting error on your part.

Glad to hear your script is up and running btw :-)

---

