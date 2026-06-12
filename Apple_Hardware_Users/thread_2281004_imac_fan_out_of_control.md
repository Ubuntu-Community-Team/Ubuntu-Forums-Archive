---
title: "imac fan out of control"
date: 2015-06-03
forum: Apple Hardware Users
---

### Post by mistywillows on 2015-06-03
I have an iMac 2009 27"   
I replaced the hard drive with a third party 4TB drive that doesn't a sensor connection to the smc.  
the fan funs at full speed all the time.

With OSX i can control the fan with [SSD Fan Control]("http://exirion.net/ssdfanctrl/"), which reads the SMART sensors


Is there any way to get the fan under control with ubuntu 15.04?

---

### Post by este.el.paz on 2015-06-03
> **mistywillows said:**
> I have an iMac 2009 27"   
I replaced the hard drive with a third party 4TB drive that doesn't a sensor connection to the smc.  
the fan funs at full speed all the time.

With OSX i can control the fan with [SSD Fan Control]("http://exirion.net/ssdfanctrl/"), which reads the SMART sensors


Is there any way to get the fan under control with ubuntu 15.04?

mw:

Might be . . . search the forum or google for posts on this forum on "macfanctl" . . . I have a thread on this topic, so you might find it under my name, and then there is a gentleman whose name is eluding me, he posted on several "fan control" threads . . . .  Might be linked in the sticky at the top of the apple hardware forum on "mactel" . . . .

Probably the ***easiest*** way to deal with fan control is to run ubuntu in Parallels or VMFusionware, or VB . . . .

e..

---

### Post by mistywillows on 2015-06-04
> **este.el.paz said:**
> mw:

Might be . . . search the forum or google for posts on this forum on "macfanctl" . . . I have a thread on this topic, so you might find it under my name, and then there is a gentleman whose name is eluding me, he posted on several "fan control" threads . . . .  Might be linked in the sticky at the top of the apple hardware forum on "mactel" . . . .

Probably the ***easiest*** way to deal with fan control is to run ubuntu in Parallels or VMFusionware, or VB . . . .

e..
macfanctl reads the smc which I already said there is no sensor for, and does not read the SMART sensors, which it would need to do ( see [https://bugs.launchpad.net/macfanctld/+bug/1019468](https://bugs.launchpad.net/macfanctld/+bug/1019468)).   I am also not interested in alternatives such as virtualization/

[**[COLOR=#000000]este.el.paz[/COLOR]**]("http://ubuntuforums.org/member.php?u=1228965")  I appreciate your willingness to help, but from seeing many of your  posts, it seems that your enthusiasm exceeds your expertise. Respectfully I ask that you let someone else answer the question.

---

### Post by Bucky Ball on 2015-06-04
You could install smartmontools from Software Centre and see if that gives you any joy. Here's some [info]("http://sourceforge.net/projects/smartmontools/").

---

### Post by este.el.paz on 2015-06-04
> **mistywillows said:**
> 

[**[COLOR=#000000]este.el.paz[/COLOR]**]("http://ubuntuforums.org/member.php?u=1228965")  I appreciate your willingness to help, but from seeing many of your  posts, it seems that your enthusiasm exceeds your expertise. Respectfully I ask that you let someone else answer the question.

@mw:

Welcome to the apple user forum . . . just trying to respond to a "one bean" poster  . . . but, no worries, other things to do with my enthusiasm . . . .

e..

---

### Post by mistywillows on 2015-06-04
> **Bucky Ball said:**
> You could install smartmontools from Software Centre and see if that gives you any joy. Here's some [info]("http://sourceforge.net/projects/smartmontools/").

looks interesting but how do you use it to control the fan?

---

### Post by este.el.paz on 2015-06-05
post deleted as Mr Mike B has stepped into the discussion.

---

### Post by MikeBraxner on 2015-06-09
Just a couple of thoughts ...

Since you'd generally not really be concerned about the heat emission from the HDD/SSD, I take it that you're interested in merely getting to grips with the fan speed/control, hence, ...

If you were running macfanctld then you could just exclude the missing, hence, erroneous sensor reading via an exclude in the config file (see man), thus side-stepping the issue ... might wanna give it a try, should work in principle.

Alternatively, you might be able to 'fake' a sensor reading by running a touch on an appropriate destination in the filesystem, followed by an echo with an acceptable value (say from rc.local) ... sounds bonkers, but what the heck.

---

### Post by DoubleClicker on 2015-07-08
> **mistywillows said:**
> looks interesting but how do you use it to control the fan?

The following script will control your fan, when you have smart tools installed.   
```

#smartfancontrol.sh

#### enter your preferred values here ##################
speed_min=1200 #RPM
speed_max=5500 #RPM
temp_min=46  #degrees celsius 
temp_max=60 #degrees celsius 

##########  Do not edit below this line ###################

echo 1 > /sys/devices/platform/applesmc.768/fan2_manual

while [ 1 ]
do

    temp=$(/usr/sbin/smartctl -A /dev/sda | grep ^194 | awk '{print $10}')
 
    if [[ $temp -lt $temp_min ]]; then
        speed=$speed_min
    elif [[ $temp -gt $temp_max ]]; then
        speed=$speed_max
    else
        x=$(($speed_max-$speed_min))
        y=$(($(($temp-$temp_min))*100))
        z=$(($(($temp_max-$temp_min))*100))
        a=$(($x*$y/$z))
        speed=$(($a+$speed_min))
    fi

    echo $speed >/sys/devices/platform/applesmc.768/fan2_output

    printf '[ %i  C | %i  rpm ]\n' $temp  $speed

    sleep 60
    done

```

---

