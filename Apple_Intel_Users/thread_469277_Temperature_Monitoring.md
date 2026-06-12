---
title: "Temperature Monitoring"
date: 2007-06-09
forum: Apple Intel Users
---

### Post by ivesjd on 2007-06-09
I've tried a few things, lm-sensors, coretemp all with no luck. I tried lm-sensors walk through on there page, yet I have not been able to view my processor temps. If anyone has gotten something working, I don't really care what, just some way of outputing processor temps, could you explain or point me to a how to. Any help would be greatly appreciated. Thanks! :)

---

### Post by ivesjd on 2007-06-13
bump

---

### Post by pveith on 2007-06-13
there a 7 temperature-sensors available under /sys/devices/platform/applesmc/ . But unfortunately they are not that readable (e.g. i don't know what the values mean exactly). You should check the values under stress and when the cpus aren't working. This shoud give you a rough indication of how well you aplle is behaving....

---

### Post by Torajima on 2007-06-14
> **pveith said:**
> there a 7 temperature-sensors available under /sys/devices/platform/applesmc/ . But unfortunately they are not that readable (e.g. i don't know what the values mean exactly). You should check the values under stress and when the cpus aren't working. This shoud give you a rough indication of how well you aplle is behaving....

Does anyone know how to convert these numbers (anywhere from 3000 to 5000) to to Celsius or Fahrenheit?

---

### Post by pveith on 2007-06-14
Found something:

```
sudo apt-get install subversion
svn co https://svn.sourceforge.net/svnroot/mactel-linux mactel-linux
cd mactel-linux/trunk/tools/temperature/
make
sudo modprobe msr
sudo ./coretemp
```

works like charm for me. 

Source: [https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

---

### Post by Torajima on 2007-06-14
Awesome. Mines at 51 degrees, which is probably cooler than when I run OSX! Then again, I've got the fans set to 5000 rpms...

Would it be possible to set the temperature result to one of the available system monitors?

---

### Post by kzm. on 2007-06-15
just a sidenote: osx runs at 43 degrees celcius with 3600rpm with me.

but isnt 5000rpm not loud?

---

### Post by Torajima on 2007-06-15
> **kzm. said:**
> just a sidenote: osx runs at 43 degrees celcius with 3600rpm with me.

This probably depends on your energy settings and what you're doing on the system. Running VMware in OSX, my Mac heats up to 63 degrees celsius (146 fahrenheit).

> but isnt 5000rpm not loud?

It's loud, but not annoyingly so. And between the TV at home and the servers next to my desk at work, I don't even hear the fan most of the time.

---

### Post by ivesjd on 2007-06-15
Thanks! It worked great. Had a small problem getting the the files from the trunk, but not bad. Its nice knowing that its not running to hot (132F on an 82F day) my fans are set to normal since I take it to classes and stuff.

---

### Post by kzm. on 2007-06-17
Torajima  you are lucky.. mine gets 73 C running vmware! ;)

---

### Post by kzm. on 2007-06-20
is there a way to have the results of ./coretemp shown in your panel through an applet?

---

### Post by ivesjd on 2007-06-20
Not that I'm aware of, if anyone finds one, please post it here.

---

### Post by ivesjd on 2007-06-26
> Is there a way to have the results of ./coretemp shown in your panel through an applet?

A sorta hackish way to do this is ```
 sudo watch ./coretemp
``` and shrink the terminal down small. Mine is about 1"x1". Not the best but it works. And you can change the colors of your terminal to customize it! :P

---

### Post by Torajima on 2007-06-26
> **ivesjd said:**
> A sorta hackish way to do this is ```
 sudo watch ./coretemp
``` and shrink the terminal down small. Mine is about 1"x1". Not the best but it works. And you can change the colors of your terminal to customize it! :P

Awesome, that works great. Here's mine:

[IMG]http://www.mindspring.com/~torajima/public/CPUtemp.png[/IMG]

I created a new terminal profile that has no menu and gave it the custom command:
> sudo watch -t coretemp

That way I can launch it without having to retype the commands every time (still have to type the password, is there a way around that?)

Note that I've copied coretemp into /bin and made it executable (sudo chmod 755 coretemp), otherwise I think you'll have to specify the full path to ./coretemp.

And if you're wondering how I converted Celsius to Fahrenheit, I just changed some of the source code:
First, change to the correct directory.
> cd ~/mactel-linux/trunk/tools/temperature

You might want to make copies of these files in case you mess something up.

Now edit the file by typing:
> gedit coretemp.c

And change:
	    > printf("CPU %d: %d °C\n", i, t);

to:
> 	    {/* add brackets */
	    t = ( t * 1.8 ) + 32; /* added to convert to Fahrenheit */
	    printf("CPU %d: %d °F\n", i, t); /* change text in string from °C to °F */
	    }

Save the file. Back in the terminal, type:
> make coretemp

Once it's done, type sudo ./coretemp and you should now see Fahrenheit rather than Celsius.

---

### Post by ivesjd on 2007-06-26
> **Torajima said:**
> Awesome, that works great. Here's mine:

[IMG]http://www.mindspring.com/~torajima/public/CPUtemp.png[/IMG]

I created a new terminal profile that has no menu and gave it the custom command:


That way I can launch it without having to retype the commands every time (still have to type the password, is there a way around that?)

Note that I've copied coretemp into /bin and made it executable (sudo chmod 755 coretemp), otherwise I think you'll have to specify the full path to ./coretemp.


I really like that. I'm gonna do a custom profile as well. There is a way to make the command coretemp work with out sudo (as in it does it automaticlly) but I dont know how. 
I actually think I'm gonna work on a gdesklet for coretemp. I'll post it here if/when I get it. Maybe this weekend.

---

### Post by kzm. on 2007-06-27
ehm.. if i want a lanucher in my panel to open the terminal and execute that line.. how would one do that?
:rolleyes:

---

### Post by mytwobears on 2007-07-10
Not sure if this is helpful but like you I could not get lm-sensors to work for me, but the acpi sensors work for me, so I installed the sensors-applet  program through synaptics.  Then I clicked on the panel - add to panel - then dragged the hardware sensors monitor icon to the panel and that will read and display the output of the acpi sensors onto your panel.  If you right click on the icon on your panel you can configure it by accessing the preferences menu.

---

### Post by ivesjd on 2007-07-24
> **mytwobears said:**
> Not sure if this is helpful but like you I could not get lm-sensors to work for me, but the acpi sensors work for me, so I installed the sensors-applet  program through synaptics.  Then I clicked on the panel - add to panel - then dragged the hardware sensors monitor icon to the panel and that will read and display the output of the acpi sensors onto your panel.  If you right click on the icon on your panel you can configure it by accessing the preferences menu.

I was just wondering what your hardware was. Not sure if you are on a mac or not, but this is in the apple forum and the acpi sensors dont work. :/ I tried what you did anyway and it didnt work (like I expected) oh well. Maybe this will help someone.

---

### Post by Eniak on 2008-03-15
I have a doubt... my temperature sensors for the cores and hard disk work completly fine, as well the fan rpm sensors... but, there are like more 11 temperature sensors that are untitled... it's like from temp1 to temp11, does anyone have any idea of what are those???

---

