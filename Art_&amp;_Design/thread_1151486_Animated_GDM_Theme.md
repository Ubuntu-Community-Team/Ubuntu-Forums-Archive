---
title: "Animated GDM Theme"
date: 2009-05-07
forum: Art &amp; Design
---

### Post by mongoosled on 2009-05-07
I'm not sure if this is the right place for this (and if it isn't, please let me know), but:


Would it be possible to create an animated GDM login theme?

By that, i mean to have a stagnant image until you log in, and then have it display a .gif or something after it has confirmed that you are a user. 

I couldn't find any animated GDM login themes on gnome-look, so i figured i'd ask here.

---

### Post by b@sh_n3rd on 2009-05-07
hmm...you mean like how the welcome screen on XP responds when you login? Nice idea...no answer though :D.

---

### Post by BslBryan on 2009-05-07
Hello, mongoosled and b@sh_n3rd. :-)

I did a bit of research, and animated GDMs, according to one source, should be supported.

This, however, is not the case.  I simply made one myself just now, and the .gif was still, and refusing to animate.

I'm sure that, with advances like Plymouth coming soon, we'll have the opportunity for animated GDMs in no time, though.

Hope I've helped.

Best to both of you. :-)

---

### Post by mongoosled on 2009-05-07
Thanks for the info, BslBryan. I'll be sure to check out Plymouth.

---

### Post by zer010 on 2009-07-31
I've been wondering about this as well.  What is Plymouth?  I guess I better get to Googling.

---

### Post by gjoellee on 2009-08-02
> **zer010 said:**
> I've been wondering about this as well.  What is Plymouth?  I guess I better get to Googling.

Google gives you all the answers :D

I ca just tell you quickly what Plymouth is. It is an animated boot screen.


When it comes to GDM, I am not sure if it is possible to create an animated login screen.
You can however create an animated login screen for "entrance", to login in manager for E17.

---

### Post by firen on 2009-08-02
How about animated wallpapers aka Windows DreamScape. Is there such a thing available for linux?

---

### Post by saam1 on 2009-08-03
You can get all answer in Google search engine....

---

### Post by Subban on 2009-08-04
> **saam1 said:**
> You can get all answer in Google search engine....

What was the point in replying?
Those answers in google come from people answering the questions in forums such as this.

@Firen
 xwinwrapper can get a screensaver running on your desktop as the background, it can be fairly effective looking though somewhat distrating when I messed with it. I don't think xwinwrapper is in the repo's but a google should locate a deb or soemthing (pretty sure thats how I had to get it a while ago)

---

### Post by shafin on 2009-08-05
Check this out, though its still WIP:
[https://wiki.ubuntu.com/DesktopTeam/Specs/GdmFaceBrowser](https://wiki.ubuntu.com/DesktopTeam/Specs/GdmFaceBrowser)

---

### Post by BslBryan on 2009-08-06
> **firen said:**
> How about animated wallpapers aka Windows DreamScape. Is there such a thing available for linux?

This script will allow you to animate a wallpaper according to the time of day.  You can edit it, of course, and make a completely new kind of wallpaper.

```
<background>

  <starttime>

    <year>2008</year>

    <month>06</month>

    <day>16</day>

    <hour>0</hour>

    <minute>00</minute>

    <second>01</second>

  </starttime>



<static>

<duration>18000.0</duration>

<file>/path/to/image/08.png</file>

</static>

<!-- il est 5h -->

<transition type="overlay">

	<duration>7200.0</duration>

	<from>/path/to/image/08.png</from>

	<to>/path/to/image/01.png</to>

</transition>

<!-- il est 7h -->

<transition type="overlay">

	<duration>7200.0</duration>

	<from>/path/to/image/01.png</from>

	<to>/path/to/image/02.png</to>

</transition>

<!-- il est 9h -->

<transition type="overlay">

	<duration>7200.0</duration>

	<from>/path/to/image/02.png</from>

	<to>/path/to/image/03.png</to>

</transition>

<!-- il est 11h -->

<transition type="overlay">

	<duration>7200.0</duration>

	<from>/path/to/image/03.png</from>

	<to>/path/to/image/04.png</to>

</transition>

<!-- il est 13h -->

<transition type="overlay">

	<duration>7200.0</duration>

	<from>/path/to/image/04.png</from>

	<to>/path/to/image/05.png</to>

</transition>

<!-- il est 15h -->

<transition type="overlay">

	<duration>7200.0</duration>

	<from>/path/to/image/05.png</from>

	<to>/path/to/image/06.png</to>

</transition>

<!-- il est 17h -->

<transition type="overlay">

	<duration>7200.0</duration>

	<from>/path/to/image/06.png</from>

	<to>/path/to/image/07.png</to>

</transition>

<!-- il est 19h -->

<transition type="overlay">

	<duration>7200.0</duration>

	<from>/path/to/image/07.png</from>

	<to>/path/to/image/08.png</to>

</transition>

<!-- il est 21h -->

<static>

<duration>10800.0</duration>

<file>/path/to/image/08.png</file>

</static>

<!-- il est 0h -->

</background>

```

And install it with this script.
```
#!/bin/sh

xml='Background.xml'
year=`date +%Y`
month=`date +%m`
day=`date +%d`
hour='0'
minute='0'

dir=`pwd`

cat <<END_OF_XML > $xml
<background>
<starttime>
<year>$year</year>
<month>$month</month>
<day>$day</day>
<hour>$hour</hour>
<minute>$minute</minute>
<second>01</second>
</starttime>

<static>
<duration>18000.0</duration>
<file>$dir/08.jpg</file>
</static>
<!-- il est 5h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>$dir/08.jpg</from>
<to>$dir/01.jpg</to>
</transition>
<!-- il est 7h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>$dir/01.jpg</from>
<to>$dir/02.jpg</to>
</transition>
<!-- il est 9h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>$dir/02.jpg</from>
<to>$dir/03.jpg</to>
</transition>
<!-- il est 11h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>$dir/03.jpg</from>
<to>$dir/04.jpg</to>
</transition>
<!-- il est 13h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>$dir/04.jpg</from>
<to>$dir/05.jpg</to>
</transition>
<!-- il est 15h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>$dir/05.jpg</from>
<to>$dir/06.jpg</to>
</transition>
<!-- il est 17h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>$dir/06.jpg</from>
<to>$dir/07.jpg</to>
</transition>
<!-- il est 19h -->
<transition type="overlay">
<duration>7200.0</duration>
<from>$dir/07.jpg</from>
<to>$dir/08.jpg</to>
</transition>
<!-- il est 21h -->
<static>
<duration>10800.0</duration>
<file>$dir/08.jpg</file>
</static>
<!-- il est 0h -->
</background>
END_OF_XML

echo "XML background file generated: $dir/$xml"

gconf=`which gconftool-2`

if [ "$gconf" != "" ]
then
$gconf --type string --set /desktop/gnome/background/picture_filename "$dir/$xml"
echo "Background automatically set"
else
echo "Please manually set the background"
fi

###END INSTALL SCRIPT
```

Just save that and make it executable, and you'll be good to go! :-)

---

### Post by firen on 2009-08-08
Thanks for the script I will try it out.

@[shafin]("http://ubuntuforums.org/member.php?u=305279") 

Thanks this is what I was looking for.

---

