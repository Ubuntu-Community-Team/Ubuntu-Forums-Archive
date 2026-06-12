---
title: "[SOLVED] scripts?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2008-01-07
Where would I put a file (script named stuff.sh) so that when I log in, I can just alt+F2 and enter: stuff
and it will execute my script? Also do I need to chmod it?

---

### Post by doorknob60 on 2008-01-07
I have a ~/bin folder that works like that, but I had to set it up myself (which I forgot how to do, sorry). You could try Google for adding folders to path in ubuntu though.

---

### Post by p_quarles on 2008-01-07
You can put it in your home folder, but then you would need to use the syntax:
```
./stuff.sh
```
in order to run it.

I believe you can also create a /bin directory in your home folder, and place it there.

To make it executable:
```
chmod u+x stuff.sh
```

---

### Post by insane_alien on 2008-01-07
shove is in /usr/bin eorks for me,

---

### Post by doorknob60 on 2008-01-07
That works but I think it's a better idea to put it in your home folder, but either way.

---

### Post by slughappy1 on 2008-01-07
I tried putting it in ~/bin/stuff.sh and chmod u+x, and I tried putting it in /usr/bin/stuff.sh and chmod u+x it again. But when I alt+F2 and type stuff, it just says "Could not open location 'file:///stuff'" "The location or file could not be found."

Oh and the file looks like this: 
#!/bin/bash

# This script starts particular screenlets and...


#My Ip Screenlet
/home/jason/.screenlets/MyIp/MyIpScreenlet.py > /dev/null
#Notes Screenlet
/home/jason/.screenlets/Notes/NotesScreenlet.py > /dev/null
#Time Screenlet
/home/jason/.screenlets/Time/TimeScreenlet.py > /dev/null
#Weather Screenlet
/home/jason/.screenlets/Weather/WeatherScreenlet.py > /dev/null

---

### Post by p_quarles on 2008-01-07
doorknob60 is correct -- for ~/bin to work, you'd have to add it to your path (/etc/environment). But /usr/bin *should* work (though /usr/local/bin would be wiser).

Is the script itself configured correctly? What happens if you just run 
```
./stuff.sh
```
from within the directory it's currently in?

---

### Post by slughappy1 on 2008-01-07
ok well that's weird. When I cd bin and then type in ./stuff.sh it loads one at a time but it loads two of them. One in the widgets layer and one on the desktop that is really small. But in order to get the others to load I have to quit one (which closes them both) and then the next one loads. What am I doing wrong?

---

### Post by p_quarles on 2008-01-07
It's hard to say without knowing what the script does. Can you post it here?

---

### Post by slughappy1 on 2008-01-07
Sorry I thought I had posted it. At least I was and then firefox crashed but anyway here it is:

#!/bin/bash

# This script starts particular screenlets and...


#My Ip Screenlet
/home/jason/.screenlets/MyIp/MyIpScreenlet.py > /dev/null
#Notes Screenlet
/home/jason/.screenlets/Notes/NotesScreenlet.py > /dev/null
#Time Screenlet
/home/jason/.screenlets/Time/TimeScreenlet.py > /dev/null
#Weather Screenlet
/home/jason/.screenlets/Weather/WeatherScreenlet.py > /dev/null

---

### Post by ryanVickers on 2008-01-07
by default anything in /bin and /usr/bin, and there might be more, will run by simply entering the name of the script.  also, you can set up a folder or file to be in your $path so it works the same way, but the easiest is just making a link in /bin or something like that...

---

### Post by p_quarles on 2008-01-07
> **slughappy1 said:**
> Sorry I thought I had posted it. At least I was and then firefox crashed but anyway here it is:

#!/bin/bash

# This script starts particular screenlets and...


#My Ip Screenlet
/home/jason/.screenlets/MyIp/MyIpScreenlet.py > /dev/null
#Notes Screenlet
/home/jason/.screenlets/Notes/NotesScreenlet.py > /dev/null
#Time Screenlet
/home/jason/.screenlets/Time/TimeScreenlet.py > /dev/null
#Weather Screenlet
/home/jason/.screenlets/Weather/WeatherScreenlet.py > /dev/null
Maybe I'm missing the point, but why are you writing these files to /dev/null? Personally, I would think a syntax like this:
```
python /home/jason/.screenlets/MyIp/MyIpScreenlet.py &
```
would accomplish your goal. Am I warm or cold? :)

---

### Post by ryanVickers on 2008-01-07
yea, /dev/null is for eating all messages, and hiding errors and stuff... to run and continue you need to append the ampersand like shown above ...

---

### Post by slughappy1 on 2008-01-08
I don't know what /dev/null even does. I just looked in my settings -> preferences -> sessions and found the command that was in there for each screenlet. If there is a better way of going about it, please let me know in detail.

---

### Post by erfahren on 2008-01-08
it would probably be better to put some delays in there between each script to give them time to start 

- also use double ampersans (they tell bash to run the next one only if the previoes succeeded) - but that's up to you 

for instance what many use to start seperate conky scripts
```

#!/bin/bash
sleep 20 &&
conky -c ~/.conky/conky_main &
sleep 22 &&
conky -c ~/.conky/conky_weather &
exit

```

putting that main script in your ~/bin *should* work, Ubuntu's (user's) ~/.bash_profile (actually named ".profile") is set up by default to set the path to the user's ~/bin if it exists. You may either need to logout and login to get it going.

or set the path and then log out/in - I sometimes have problems getting mine to work on a fresh install but it starts working after I mess with it. for more info on that see: [http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)

---

### Post by slughappy1 on 2008-01-08
what is conky?

---

### Post by whiteraven on 2008-01-08
Add the following line to the end of your ~.bashrc

  export PATH=$PATH:/home/directory_name

Substitute your actual directory name where the script is located.

Make sure you chmod +x script_name, and you're good to go!

---

### Post by slughappy1 on 2008-01-08
you meant ~/.bashrc right?

---

### Post by slughappy1 on 2008-01-08
ok well I made a folder /home/username/bin and put my file (stuff) in there. The file contains:
```
#!/bin/bash

# This script starts particular screenlets and...

#My Ip Screenlet
#python /home/jason/.screenlets/MyIp/MyIpScreenlet.py &
#Notes Screenlet
#python /home/jason/.screenlets/Notes/NotesScreenlet.py &
#Time Screenlet
python /home/jason/.screenlets/Time/TimeScreenlet.py &
#Weather Screenlet
python /home/jason/.screenlets/Weather/WeatherScreenlet.py &
```
I then went into the ~/.bashrc and added ```
export PATH=$PATH:/home/username/bin
```
I then proceeded to ```
chmod +x stuff
```
And it would appear to be working perfectly like I wanted to. Thanks for all of the help

---

### Post by erfahren on 2008-01-08
> 
what is conky?

[Conky - A light-weight system monitor](http://conky.sourceforge.net/)

see the conky (mega)thread: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
__________________________________________________________________________________

> **whiteraven said:**
> Add the following line to the end of your ~.bashrc

  export PATH=$PATH:/home/directory_name

Substitute your actual directory name where the script is located.

if you use a ~/bin that isn't necessary

the .bash_profile (~/.profile in Ubuntu) by default already has:
```

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

```
you can also put the direct path to the startup script in the Sessions Startup (I think the OP originally had it that way, but had problems with the script itself) - a ~/bin does come in handy though
_

---

