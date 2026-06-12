---
title: "Disabling  Touchpad"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by pyromunky on 2007-04-21
My first post, and I just want to start off by saying thank you. I went into this install of fiery without any prior knowledge of linux, and these forums have been extremely helpful.

One question I wasn't able to find an answer to though... How can I disable the touchpad on my laptop completely? So all I am able to use is my usb mouse. I have a short in my touchpad that causes my cursor to drift when I am typing certain keys, so I want to try disabling it all together.

Thanks...

---

### Post by leibowitz on 2007-04-21
What you are talking about is called synaptic (I don't care either the name, but it will helps you when you need to find information about that on linux).

And AFAIK you need to tweak the Xorg configuration file, which is located in /etc/X11/xorg.conf

There you can put many configuration to the synaptic touch pad device, and maybe disable it for good. I don't have any laptop to try this. So I will just say good luck with that because it's prety hard to guess what configuration is needed.

Maybe you can try installing gsynaptic, but I don't know if it will be of any help here.

---

### Post by leibowitz on 2007-04-21
I may have found something interesting.

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

There it is said that you need to add this line in your configuration file to handle the synapticsTouchPad. Then what YOU need is to delete just that line :-)

```
InputDevice     "Synaptics Touchpad"
```

It will be located at the end of the /etc/X11/xorg.conf file.

So edit it with this command. From the Applications menu, go to Accessories, Terminal. And paste this:

```
gksudo gedit /etc/X11/xorg.conf
```


Now find the previous line (input device synaptics...) and just put a "#" character at the left of this line. So it becomes this:
```
# InputDevice "Synaptics TouchPad"
```

Save the file, and quit.

Now restart your computer and you should not be annoyed anymore with the touchpad. I know, that's not an easy way to disable the touchpad.

---

### Post by pyromunky on 2007-04-22
Thanks for the suggestion. Following the instructions in the link you provided, I get an error that the X server failed to start after rebooting.

---

### Post by briniel on 2007-04-22
> **pyromunky said:**
> Thanks for the suggestion. Following the instructions in the link you provided, I get an error that the X server failed to start after rebooting.

try:

$ sudo dpkg-reconfigure -phigh xserver-xorg

that should restore the default xorg.conf file.

---

### Post by pyromunky on 2007-04-22
Thanks again for all the suggestions. I ended up using gsynaptic. TouchPad is now disabled completely. Bu the problem is still there. Digging a little deeper, I find out it's the stick mouse causing it. Any ideas on how to pinpoint this input device and disable it as well?

---

### Post by leibowitz on 2007-04-22
> Any ideas on how to pinpoint this input device and disable it as well?
Check into your /etc/X11/xorg.conf file for InputDevice sections. It should be there aswell.

Finally I don't understand how X was broken with only one line commented. You said you followed instruction on the link. But you didn't have to. If you have any more trouble please join your xorg.conf file in here.

---

### Post by pyromunky on 2007-04-22
I had tried disabling the touchpad by commenting out the line in xorg as you suggested, but it didn't work. So I moved on to the on/off key method in the link you posted. That's what caused the x server error. 

The problem is resolved now though. Turns out the pointer stick issue is hardware related. So I popped off the keyboard, disconnected the stick and no more floating mouse. "Maming" a Dell is actually quite therapeutic...

Thanks again for all your help guys.

---

### Post by leibowitz on 2007-04-22
oh.. I see. Sorry for providing the link :-) As  it didn't help at all.

---

### Post by pyromunky on 2007-04-22
No worries. I appreciate the help. It's a learning experience...

---

