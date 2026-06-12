---
title: "script only works if I type it manually"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by bsmith1051 on 2006-04-27
I've got a siiiiimple shell script to load vsound, realplay, and the URL of my favorite radio program.  No matter what I try -- Run in Terminal, or Run -- the realplay app gives a general error.  But if I copy-and-paste the command into terminal, it works fine.  I don't understand what's different, i.e., between typing (pasting it) and having it in a .sh file.

I also tried opening a terminal and running the file,
 > ./record.sh
same error...

---

### Post by Qrk on 2006-04-27
You should paste the script here or no one will be able to help.

---

### Post by bsmith1051 on 2006-04-27
oh, sorry.  Here's what it looks like.  Every day, I just update the date reference:
> vsound --file=today.wav realplay [http://www.publicradio.org/tools/media/player/noads/marketplace/2006/04/27_mpp.smil](http://www.publicradio.org/tools/media/player/noads/marketplace/2006/04/27_mpp.smil)

---

### Post by ComplexNumber on 2006-04-27
the script MUST start with "#!/bin/bash"(without the quotes) as the first line.

---

### Post by audax321 on 2006-04-28
Also if you change the script to this it should automatically put in the current year in four digit format, month in two digit format (01...12), and current day in two digit format (01...31) so you don't have to edit it everytime:

```

#!/bin/sh

vsound --file=today.wav realplay http://www.publicradio.org/tools/media/player/noads/marketplace/"$(date +%Y)"/"$(date +%m)"/"$(date +%d)"_mpp.smil


```

---

### Post by gr0kzer0 on 2006-04-28
I hope I'm not stating the obvious here, but your shell script has to be executable. The command ```
chmod +x shell.sh
``` would make it so (substituting your script's name for shell.sh of course).

---

### Post by bsmith1051 on 2006-04-28
wow, great.  Thanks!  I obviously know nothing about scripting.  I already had it marked 'executable' but the part about "#!/bin/bash" totally new to me.

Can someone explain why it's necessary?  For instance, if I run this from a terminal, it's already in bash, right?

---

### Post by yomoenco on 2006-04-28
It tells the shell what kind of interpreter to start (Perl, ksh, bash, .....)

Regards,
   Andre

---

### Post by audax321 on 2006-04-28
It's needed to tell the terminal how to execute the script/what kind of script it is. The "#!/bin/bash" and "#!/bin/sh" arguments tell linux that the script is a shell script. If you were writing a python script for instance it would start with something like "#!/usr/bin/env python"

---

### Post by bsmith1051 on 2006-04-28
ugh.  still doesn't work.  In every instance (including my original bash-less version), terminal opens-up, vsound says it's loaded and waiting ... but then RealPlayer (v10) reports simply, "General Error."  No other info.  Same command, manually run from terminal, RealPlayer is totally happy.  It's as if 'vsound' is spinning-off a new instance, or something, which does not have the proper permissions.  

I also tried using 'sudo vsound...' in the script.  This time, Real Player did a first-time user setup.  Then it failed, same way as always.

---

### Post by audax321 on 2006-04-29
Hmmm, not sure why it's not working for you. I just downloaded VSound and it worked fine for me. I ran it the following ways:

1. Put it in /home/user/.gnome2/nautilus-scripts and ran it from right-click menu.
2. Ran it from Run dialog (sh /path/to/script.sh) both with "Run in Terminal" option checked and unchecked.
3. Ran it from within terminal (sh /path/to/script.sh)

I used both #!/bin/sh and #!/bin/bash and never encountered a problem.

There must be something wrong with your script unless I'm missing something here. Check the following:

1. Find your script, right-click on it and choose Properties. Go to the permissions tab and click the checkboxes until the permissions are 755 (all Read checked, top Write checked, all Execute checked)
2. Copy and paste your script here using the CODE button on the reply to thread screen (it's the # image).

---

### Post by bsmith1051 on 2006-05-01
```
#!/bin/bash
vsound --file=today.wav realplay http://www.publicradio.org/tools/media/player/noads/marketplace/2006/04/28_mpp.smil


```
Remember, it's not 'vsound' that's failing, it's Real Player.  It appears to load correctly, but then it pops-up an error, "A general error has occurred."  Maybe the URL isn't getting passed to it correctly?  As an experiment, I tried putting double-quotes around the URL (the final expression in the 'vsound' command-line) but it's still the same error.

---

### Post by zerhacke on 2006-05-01
Try substituting "start" for "realplay".. without the quotes of course.

---

### Post by bsmith1051 on 2006-05-04
[QUOTE=zerhacke]Try substituting "start" for "realplay".. without the quotes of course.[/QUOTE]
Good idea but it doesn't work.  I tried manually doing "vsound --file=today.wav start  etc-etc.smil" and it reports "start: command not found".  Maybe I need to register .smil somehow?  nyah, I just tried it with a standard URL, i.e., "start http://www.yahoo.com" and it didn't know what to do with that either.

---

