---
title: "running command on startup ?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by justino on 2006-06-07
Hi all!

I just managed to get my laptop dual booting xp and ubuntu (hurrah!) and also managed to find a program that tricks the intel gma into using the correct resolution.

I know there's a way to run these items at startup, I did a bit of searching around before posting and found that rc.local can be changed to run things on startup and also the sessions editor should do the same thing.  

The trick about this is that i need to run the program before x starts (else I have to restart x to get the resolution fix to work)

so what I need to happen is something like 

"sudo 915resolution 5c 1280 800" 

Is there any place that I could put that so that it runs before x starts so I don't need to do the ctrl + alt + backspace thing every time I login ?

Thanks! 

Justin

ps- My terminology might be a bit off this is my first time giving linux a go...

---

### Post by patrick295767 on 2006-06-07
[QUOTE=justino]Hi all!

I just managed to get my laptop dual booting xp and ubuntu (hurrah!) and also managed to find a program that tricks the intel gma into using the correct resolution.

I know there's a way to run these items at startup, I did a bit of searching around before posting and found that rc.local can be changed to run things on startup and also the sessions editor should do the same thing.  

The trick about this is that i need to run the program before x starts (else I have to restart x to get the resolution fix to work)

so what I need to happen is something like 

"sudo 915resolution 5c 1280 800" 

Is there any place that I could put that so that it runs before x starts so I don't need to do the ctrl + alt + backspace thing every time I login ?

Thanks! 

Justin

ps- My terminology might be a bit off this is my first time giving linux a go...[/QUOTE]

quickly:

you can look there :   
**/etc/rc2.d/**[COLOR="Red"]**SXX**[/COLOR]lkfjmsdfl.sh
XX is the level 
and SXXlkfjmsdfl.sh the script

look in man pages ...

---

### Post by Kryptizzle on 2006-06-07
Try this. 

- System > Preferences > Sessions > Startup. 
- Click add, and paste the command.

I'm not sure if it's what you're looking for though.

Edit: Nvm, I didn't read the bit about starting it before x.

---

### Post by Kobalt on 2006-06-07
Hi, 

Is what you want to change the resolution of the bootsplash, or do you have a blank screen and you actually want to see the bootsplash ?

---

### Post by xtacocorex on 2006-06-07
I would do this:

First create the file /etc/cron.allow 
```
sudo touch /etc/cron.allow
```
and in it type (using your favorite editor as root):
```

root
justino

```
(I'm assuming that justino is your computer's username)

I would then create a bash file in ~/bin and call it reschange and make sure it has execution permissions with: 
```
chmod +x ~/bin/reschange
```

The ~ is a another way of denoting /home/justino.

reschange should have the following in it (again, type with your favorite editor, but as normal user):
```

#!/bin/sh

915resolution 5c 1280 800

```

After you do all of this, I would then do:
```

sudo crontab -e

```

When the system crontab editor opens up, type:
```
@reboot /home/justino/bin/reschange
```

Then exit the editor. I'm not sure what editor it [crontab -e] brings up by default, but if it is vi, then to exit and save, you need to hit the <ESC> key, then <SHIFT> + ; to get a : and then type wq at the : prompt. I'm again assuming that your username is justino.

What this does it:
1) Allows the root and you to run cron jobs. Ubuntu by default doesn't do so.
2) Creates a shell script to control the command that you want to run
3) Sets up a cron job at reboot that will run the script. 

I can't test this because I don't need 915resolution for my laptop, but I do know that the cron jobs are run during the init process, so this should work.

EDIT: Made minor changes to make information clearer.

---

