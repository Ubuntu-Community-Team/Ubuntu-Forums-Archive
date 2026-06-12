---
title: "Shell script question"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by fontenot_1031 on 2007-07-07
I have just downloaded Nexiuz and want to make a launcher for it.  The game is in the path /home/me/.Nexiuz.  I was wondering how it would be possible to have a launcher that would run the shell script nexiuz-linux-686.sh; which starts the game.

---

### Post by pbaumgar on 2007-07-07
> **fontenot_1031 said:**
> I have just downloaded Nexiuz and want to make a launcher for it.  The game is in the path /home/me/.Nexiuz.  I was wondering how it would be possible to have a launcher that would run the shell script nexiuz-linux-686.sh; which starts the game.

Just make the path to /home/me/.Nexiuz/ nexiuz-linux-686.sh

---

### Post by fontenot_1031 on 2007-07-07
I've already tried that as a command.  Also ./nexiuz-linux-686.sh doesn't work either

---

### Post by ape on 2007-07-07
What error messages are you seeing?

if you try to run nexiuz-linux-686.sh by hand what happens?  Any messages?  What are the permissions on nexiuz-linux-686.sh?

--ape--

---

### Post by Kingsley on 2007-07-07
I'm not sure. Maybe you have to make the launcher executable. ```
chmod a+x /home/me/.Nexiuz/ nexiuz-linux-686.sh
```

---

### Post by pbaumgar on 2007-07-07
did you download the .zip file and extract it?

try:

sh exiuz-linux-686.sh

---

### Post by fontenot_1031 on 2007-07-07
> **Kingsley said:**
> I'm not sure. Maybe you have to make the launcher executable. ```
chmod a+x /home/me/.Nexiuz/ nexiuz-linux-686.sh
```
Hmm, that doesn't seem to do the trick either

---

### Post by fontenot_1031 on 2007-07-07
> **ape said:**
> What error messages are you seeing?

if you try to run nexiuz-linux-686.sh by hand what happens?  Any messages?  What are the permissions on nexiuz-linux-686.sh?

--ape--

Just clicking on the actual .sh file works.  It asks me if I want to run in terminal or run.  The game works that way

---

### Post by Alterax on 2007-07-07
Try running it as an application in a terminal (drop-down menu has it as an option).
Then in command, put in the FULL path to the shell script.

Let's say I wanted to make a launcher for Second Life.  Since I am a bit of a slob, I've extracted the file into a directory called SecondLifeVersionNumber in my home directory (not the best practice, I know).  The command to run it is secondlife.

If I were to run it from the shell in the directory, I would just type ./secondlife and off it goes, because the filesystem already knows where I am.

But for making a launcher in my case, I would give the absolute (or full) path to the secondlife launcher, starting from / 

/home/myusername/SecondLifeVersionNumber/secondlife

To get the full directory, here's a neat way to do it.  Go into the directory you have to run the shell script from.
Now type pwd   (for Print Working Directory).  This shows you the full path of the directory you are in.  Throw a slash on the end of that, followed by the name of the file you are trying to run, and there you have it.

Let me know if this helps.

--Alterax

---

### Post by RomeReactor on 2007-07-07
Hi. Try filling out the **Command** section of the launcher like this:
```
sh -c "cd /home/me/.Nexiuz/ && ./nexiuz-linux-686.sh"
```
or
```
sh -c "cd /home/me/.Nexiuz/ && sh nexiuz-linux-686.sh"
```

---

### Post by Alterax on 2007-07-07
Using sh would be a redundancy.  The beginning of a shell script states which shell is to run the commands.  Easier to just give the full path and let the OS do the figuring for you.

---

### Post by pbaumgar on 2007-07-07
> **Alterax said:**
> Using sh would be a redundancy.  The beginning of a shell script states which shell is to run the commands.  Easier to just give the full path and let the OS do the figuring for you.

giving the full path to the the shell script is the same is as sh <script>...

it's not redundant... it's where you run the script from.

---

### Post by fontenot_1031 on 2007-07-07
Thank you everybody for your wonderful responses, you've truly helped a new Linux convert!

---

### Post by fontenot_1031 on 2007-07-07
> **RomeReactor said:**
> Hi. Try filling out the **Command** section of the launcher like this:
```
sh -c "cd /home/me/.Nexiuz/ && ./nexiuz-linux-686.sh"
```
or
```
sh -c "cd /home/me/.Nexiuz/ && sh nexiuz-linux-686.sh"
```I got a little bit closer to getting it to run with that last command.  I chose to run it as an application in terminal and the terminal popped up for a second.  Then closed with out the could not file file error

---

### Post by iver2435 on 2007-07-07
Also you could try putting "bash" in front of it, like:

```
bash nexiuz-linux-686.sh
```

The previous poster had you using "sh" instead of "bash" which could be why it was bombing out....

---

### Post by Ayuthia on 2007-07-07
There should not be a need to use sh or bash in front of a shell script that you are trying to run.  The thing that you do need is to put the path of where your program is located.  So if you are trying to run xyz.sh from /home/user you would need to do:
/home/user/xyz.sh
or if you are in the current directory you can type:
./xyz.sh

The reason why sh or bash would work is because sh and bash are located in /bin is is something that is found in your $PATH.  The system will always look for programs that are located in $PATH  unless you give it a path to look at.

---

### Post by RomeReactor on 2007-07-07
> **fontenot_1031 said:**
> I got a little bit closer to getting it to run with that last command.  I chose to run it as an application in terminal and the terminal popped up for a second.  Then closed with out the could not file file error

Don't run it as an **Application in Terminal**, just as **Application**. It *should* work, I've made at least a dozen launchers like this.

Also, this may sound silly, but...
```
sh -c "cd /home/**me**/.Nexiuz && sh nexiuz-linux-686.sh"
```
Remember to add the correct name of your home folder (assuming it isn't **/home/me**).

---

