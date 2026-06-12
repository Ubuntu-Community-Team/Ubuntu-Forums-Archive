---
title: "Need scripting help"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Brendantb on 2007-04-02
Hi, 

I currently don't have automatic control of the fan on this old machine. I've installed the lm sensors, which do a good job of detecting the chip and board heat, and I have also installed the toshset fan controls which allow me to manually turn the fan on and off if I remember!

I have set up a little fan icon in the panel to turn on the fan with the terminal command: 

"sudo toshset -fan on" 

The command for off is:

"sudo toshset-fan off" 

I would like to set up a script such that clicking the fan icon will toggle between fan on and fan off. There is a state file in /proc/acpi/toshiba/fan which has two entries: 

running:                      0
force_on:                    0

which changes depending on whether the fan is on, "1" or off, "0." 

I was hoping to use this as the basis for a condition script to make the fan click into a toggle. 

I would also like this process to be made to run "as root" so that I don't have to put in my password, if at all possible, but that would be jam on it... :) 

Hoping that someone with a bit more experience can give me a few pointers...

---

### Post by Bachstelze on 2007-04-02
Here you go. As you can see, it does not use sudo so you need to run it with sudo/gksudo.

```

#!/bin/bash

function fanToggle()
{
        #What do you want to do today ? Oops, I guess that line
        #is covered by software patents from M$...

        if [ `cat /proc/acpi/toshiba/fan | grep running | \
           awk '{print $2}'` == "1" ]; then

                echo "Fan is running, I'll disable it.";
                toshset -fan off

        else

                echo "Fan is not running, I'll enable it.";
                toshset -fan on

        fi
}

if [ `whoami` == "root" ]; then #Are you root ?

        fanToggle

else

        echo "You are not root."

fi

```

---

### Post by Brendantb on 2007-04-02
Hi, 

that looks to be exactly what I was looking for!

Unfortunately, I am not sure of the sudo/gksudo command. Could you please expand a little on what I should do to utilise this script properly? Sorry to appear so clueless...

---

### Post by bashologist on 2007-04-02
Maybe this would work:
```
#!/bin/bash
gksudo toshset -fan on || gksudo toshset-fan off
```
Then execute the script from your panel maybe? If trying to turn it on when it's on returns false then this might work.

---

### Post by Bachstelze on 2007-04-02
For example, if you saved it as fan.sh in your home dir, you just need to do :

```
sudo sh ~/fan.sh
```

another option would be to put it somewhere in your $PATH, for example :

```
sudo cp fan.sh /usr/local/bin
sudo chmod +x /usr/local/bin/fan.sh
```

Then you can run it with just *sudo fan.sh* in a terminal or *gksudo fan.sh* from the Run dialog or a launcher.

---

### Post by Brendantb on 2007-04-03
Hi, 

I made a file in /usr/local/bin/ called fan.sh, and pasted in that script, made it executable, then put the sudo fan.sh command in the launcher, and it works exactly as it should: clicking the icon toggles the fan off and on. 

Thank you for your assistance.

---

