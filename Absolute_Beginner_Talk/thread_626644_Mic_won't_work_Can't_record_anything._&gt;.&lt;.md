---
title: "Mic won't work/ Can't record anything. &gt;.&lt;"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by ShumakerKH on 2007-11-29
Ok, I am not really a newbie here, I know a bit about computers and I have been running Ubuntu for a while and have come to be quite comfortable with it. I am however having one problem that I haven't been able to fix on my own, or with the help of posts on here. I cannot get my mic to record anything, and I keep getting error messages when I try to configure it. I have a Dell Latitude D820 with a built in microphone. 
When I try to run *Sound & Video > Sound Recorder* I get "Your audio capture settings are invalid. Please correct them in the Multimedia settings." and I cannot get around that. 
Any ideas, or fingers pointing me in the right direction, or other ideas of programs to use will me immensely helpful. I'm trying to record my History lectures because I cannot follow my professor to save my own butt.

Thanks.

---

### Post by mahiyar on 2007-11-29
If you have seen a lot of tips and none seem to help .....
1) Like I always keep the recording source as microphone or line-in, not both.
2)The microphone volume is not off.
3)Try using the +20db microphone boost.

etc. etc. The only other thing I can think of is I had the problem when I installed pulse_audio. Look at my post here [http://ubuntuforums.org/showthread.php?t=579529](http://ubuntuforums.org/showthread.php?t=579529)

---

### Post by ShumakerKH on 2007-12-01
Thanks, with that and a little extra tweaking, I got it working. ^.^

---

### Post by mahiyar on 2007-12-01
Can you post the extra bit of tweaking you did so that it could be of help to others. Thanks

---

### Post by ShumakerKH on 2007-12-02
Well, now that I got the recording working and the other audio glitches fixed, I can't get any sound in Skype, incoming or outgoing. >.<

---

### Post by Nethippy on 2007-12-02
For skype, Load skype and try going to tools/options and from the sound section, check that OSS device is selected and that audio in/out and ring are set to /dev/dsp.

---

### Post by ShumakerKH on 2007-12-03
ok, Multimedia settings is no longer in my Menu, and i can't find it anywhere. is there any other way to open Multimedia settings than through the menu?

---

