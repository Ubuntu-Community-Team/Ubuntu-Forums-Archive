---
title: "[SOLVED] Automatically start playing when Rythmbox starts"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by AlistairH on 2008-02-17
Is there a command line option that will tell Rythmbox to automatically start playing a song when ever Rythmbox is launched?

---

### Post by kelbizzle on 2008-02-18
The command to make rhythmbox start playing is 
```
rhythmbox-client --play
```

I found that using the "man rhythmbox-client" command to see any option I could use with the command.

---

### Post by AlistairH on 2008-02-20
Thanks kelbizzle.

Unfortunately, that's not quite what I'm looking for. The code above only works when Rhythmbox is already running. I'm looking to make Rhythmbox start playing whenever I launch it from the menu.

Replacing the standard launch command with the above simply loads Rhythmbox but it doesn't start playing.

---

### Post by erginemr on 2008-02-20
As a workaround, you can do the following:

1. Copy the attached simple script that I have written to your home folder and extract it:
```
cd ~
tar xvzf r-play.tar.gz
```

2. Give execute permissions to the script.
```
chmod a+x r-play
```

3. You can check its contents with:
```
gedit r-play
```
Inside the script, you will see:
```
#!/bin/bash
# a script to play Rhythmbox automatically
rhythmbox &
sleep 1
rhythmbox-client --play &
```

Here is the story: 

**"rhythmbox-client --play"** works only if there is a running instance of rhythmbox. So, we need to run **"rhythmbox &"** first, allow enough time to it to start with **"sleep 1"** (i.e. wait for 1 sec, you can play with this value), and finally run **"rhythmbox-client --play &"** to manipulate the already running instance of the program. The sign (&) is to put the application to the background, so that the script can continue with the next command. 

You can try it with:
```
./r-play
```
You should have an active playlist for it to work. The part (./) is needed to run a local script existing in the same directory.

4. Now, if everything works as expected, move it to your "/usr/bin" directory:
```
sudo mv r-play /usr/bin
```

5. Try if it works from the terminal:
```
r-play
```

6. If it does, then you can create a launcher or alter the existing one with just "r-play" as the command.

---

### Post by laidback on 2008-02-20
If you default any music file (e.g. .mp3, .ogg) to start with Rythmbox than by clicking on the file SHOULD launch Rythmbox and start playing the music chosen. 
To  default to Rythmbox, in Nautilus (file manager) right click any file of the required type (e.g. mymusic.mp3), select Properties>Open With tab and then click the appropriate radio button.
Now when you select ANY music of that type Rythmbox should launch and play the music.

However, I was playing with this idea and Rythmbox just that other day and on my machine it only plays the music for about 10secs and then stops. With Amarok it works just fine. After a deal of messing around I concluded that with Rythmbox it just doesn't work. I prefer Amarok anyway and was only trying it out to aid another user.

Good luck

---

### Post by AlistairH on 2008-02-20
Thanks for the replies folks. I think the script option is the one for me. Cheers

---

