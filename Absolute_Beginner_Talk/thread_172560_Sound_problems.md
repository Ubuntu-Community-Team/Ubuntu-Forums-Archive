---
title: "Sound problems"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by mrkeef on 2006-05-08
I've just installed Ubuntu 5.10 from the CD on two computers, one desktop the other a lap top with same result on both.

The speaker applet on the tool bar has  a cross next to it.

When I try to play an audio CD I get this message: The currently selected audio profile is not available on your installation."

Sound juicer comes with the message "The plugin necessary for playing CDs could not be found."

clicking on the sound applet I get "Registry is missing or is corrupted. Please update it by running gst-register."

In synaptic all the gstreamer packages from the CD have been installed.

Can someone point me towards a way of getting sound running properly?

Thanks.

---

### Post by ComplexNumber on 2006-05-08
go to the commandline and type in 'gst-register'

---

### Post by mrkeef on 2006-05-09
[QUOTE=ComplexNumber]go to the commandline and type in 'gst-register'[/QUOTE]
I tried that, but it couldn't find gst-register.

I did a search but still couldn't find it.

---

### Post by deadgobby on 2006-05-09
[https://wiki.ubuntu.com/DebuggingSoundProblems?highlight=%28sound%29](https://wiki.ubuntu.com/DebuggingSoundProblems?highlight=%28sound%29)
[http://ubuntuforums.org/showthread.p...ighlight=sound](http://ubuntuforums.org/showthread.p...ighlight=sound)
[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)
[https://wiki.ubuntu.com/?action=full...&titlese](https://wiki.ubuntu.com/?action=full...&titlese) arch

Here are some links to trouble shoot your problem. I hope one of them are you cure. 
 Are you installing a Dell systems? One your PC, does it have a built in sound card? What is your laptop brand name? Some of the questions may help.
Gobby

---

### Post by Sef on 2006-05-09
Did you install the codecs from Restricted Formats?

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

Also you may need to click on the speaker icon on top right and highlight Open Volume Control.

---

### Post by mrkeef on 2006-05-16
When I right click on the speaker icon and highlight Open Volume Control I get "No volume control and/or devices found"

Thanks

---

