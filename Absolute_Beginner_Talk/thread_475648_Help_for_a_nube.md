---
title: "Help for a nube"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by traveler-1 on 2007-06-16
While trying to install Moneydance I got the following error. How do you correct it. I get the same error with both  option's I have

[http://s202.photobucket.com/albums/aa15/traveler-1/?mediafilter=images](http://s202.photobucket.com/albums/aa15/traveler-1/?mediafilter=images)

---

### Post by jimbob on 2007-06-16
Why don't you try to run that moneydance ...........sh script from a terminal window and see what it does.

Open a terminal and type: ./moneydance ....   .....sh

(fill in the rest of it where I put in the dots of course)
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by traveler-1 on 2007-06-16
This is what i tried

mike@mike-desktop:~$ ./moneydance_linux_x86wj.sh
bash: ./moneydance_linux_x86wj.sh: No such file or directory
mike@mike-desktop:~$

Still doing something dumb:(

---

### Post by jimbob on 2007-06-16
First you have to find it.  In a terminal window type in:  [I][COLOR="RoyalBlue"]locate moneydance
[/COLOR][/I]
What did it come up with?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by sessine on 2007-06-16
You are in the wrong directory in your terminal.  The screenshot shows the file is in your Desktop folder but you issued the command from your home directory.

In the terminal try 'cd Desktop' and then execute the command.

---

### Post by traveler-1 on 2007-06-16
Here you go.
mike@mike-desktop:~$ locate moneydance
/home/mike/Desktop/Screenshot-moneydance_linux_x86wj.sh (~-Desktop) - gedit.png
/home/mike/Desktop/moneydance_linux_x86wj.sh
mike@mike-desktop:~$ 

BTW; Thanks for the help. Quickest answers I HAVE ever gotten.:p




> **jimbob said:**
> First you have to find it.  In a terminal window type in:  [I][COLOR="RoyalBlue"]locate moneydance
[/COLOR][/I]
What did it come up with?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by traveler-1 on 2007-06-16
Are you sure CD works in linux. I got no where with it. 

Found the command it is cd ~/Desktop.

Thanks


> **sessine said:**
> You are in the wrong directory in your terminal.  The screenshot shows the file is in your Desktop folder but you issued the command from your home directory.

In the terminal try 'cd Desktop' and then execute the command.

---

### Post by GrueTamer on 2007-06-16
You don't run shell scripts with the normal ./, you need to tell the terminal that it's a shell script with sh.  So, try...

```
sh moneydance_linux_x86wj.sh
```

---

### Post by traveler-1 on 2007-06-16
Got this

mike@mike-desktop:~$ sh moneydance_linux_x86wj.sh
sh: Can't open moneydance_linux_x86wj.sh
mike@mike-desktop:~$

The file is setting on the desk top or at least I see it there ;)

Thanks

Lots to learn here !


> **GrueTamer said:**
> You don't run shell scripts with the normal ./, you need to tell the terminal that it's a shell script with sh.  So, try...

```
sh moneydance_linux_x86wj.sh
```

---

