---
title: "MIddle Mouse Button (Logitech Cordless Click)"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Jay_in_TN on 2007-06-19
I have searched quite a bit. I have found several threads regarding 5-button mice. I have a 3-button, optical, cordless click mouse by Logitech. It has a small, middle mouse button which is defaulted to "back" function in the Windows platform.
I would like to tell it to be "back" in Ubuntu.
Is there a simple way to do this?
Perhaps someone could point to a HowTo that I missed?
Thanks,
Jay

---

### Post by atria on 2007-06-20
The method is not exactly easy, but its not that hard either.
Install imwheel and configure it to change the behaviour of your wheel button. The profile can even be applied to different programs.

I'm rushing for time now so i won't be able to tell you the specifics. Try searching for imwheel in the forums.

Good luck!

---

### Post by Jay_in_TN on 2007-06-20
Thank you for your reply. However, it is not my wheel button that I want to change. I have a very small button on the top of the mouse, just behind the wheel that is the "3rd" mouse button. It is the one that I want to program to be a "back" button in Ubuntu.
Like most of my complaints with Linux (which I fully support and would like to implement in my school) sometimes I think (what should be) simple issues are just a bit too difficult.

I am not a programmer, but programmers have created literally thousands of applications for the Linux platform, but installing a VERY common mouse like the cordless click is a giant problem. WTF? Perhaps it would be better if these guys coded simple, graphical drivers and hardware apps like the ones that make using Windows such a simple procedure. Another example: To access the nvidia (the most common video card in use today) settings, you have to hit alt+F2, then type in sudo nvidia-settings! What the hell is up with that? The nvidia graphical interface should appear in the System/Administration so the average user can find it. Dontcha think?

Again--I really like Ubuntu and it is installed on all of my computers. But sometimes the seemingly little things can be way too complicated.
As I have said over and over: It should not be this difficult.
Thanks for any other suggestions that anyone can offer.
Jay

---

### Post by orb9220 on 2007-06-20
> To access the nvidia (the most common video card in use today) settings, you have to hit alt+F2, then type in sudo nvidia-settings! What the hell is up with that? The nvidia graphical interface should appear in the System/Administration so the average user can find it.

Mine is in System Tools>Nvidia Settings

A Search in google **ubuntu logitech mouse** gives [http://www.google.com/search?q=ubuntu+logitech+mouse&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=ubuntu+logitech+mouse&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by atria on 2007-06-20
Precisely, you need imwheel to map the 3rd mouse button to the "back" function.

Heres how to do it:

Firstly, install imwheel with ```
sudo aptitude install imwheel
```

After that, execute "imwheel -c" in your console (without the quotes) and a small window should open. Right in the window, press GrabWheelAction, then press the your third mouse button to view its default mapping. Let this default mapping be <mousebutton> which is mentioned below.

Next, create a .imwheelrc file inside your home directory
```
nano -w ~/.imwheelrc
```

and paste the following code into it:
```

"^Firefox-bin$"
None, <mousebutton>, Alt_L|Left

```

Do remember to replace <mousebutton> with what you got from imwheel -c just now. 
After that close the file and save it. 

Finally start imwheel:
```
imwheel
```

The above configuration that i have given you works specifically for firefox, that is, you press the button to go back to the previous page.

It can be easily customised for use with other programs as well, just add the relevant sections and map the keys appropriately.

Hope that helps

---

### Post by Jay_in_TN on 2007-06-22
Thanks again for the replies.
Oddly--I do not have a "system tools" options in my menus. I will dig around and try to add it.

As for imwheel: thanks A LOT for the howto. Unfortunately, after getting and unpacking the app, typing imwheel-c doesn't do anything. I dug around until I found the imwheel directory (it is in usr/lib) then I changed to that directory and it is still a "command not found" error,

I dug around the directory and did not find the actual executable for imwheel.

Hummm. I am stumped.

Jay

---

### Post by Jay_in_TN on 2007-06-22
Regarding nvidia-settings:

I used system/preferences/main menu to edit the options in the main menu.

System Tools needs to be opened on the LEFT side of this interface and all the sub-options checked. Then "system tools" can be checked on the RIGHT side of the interface and it will appear under "Applications."

However, the nvidia-settings option still did not appear in the menu. This required going back to system/preferences/main menu and selecting "system tools" on the LEFT side of the interface, then clicking "new item" on the FAR RIGHT side of the interface. Then I had to point to usr/bin/nvidia-settings for the application to both show up in the list and to be functional. This should work for anyone else who wishes to add the nvidia gui to their system tools menu.

Not sure why Orb9229 already had the gui in his system tools and I did not. Hummm.

Any suggestions on the mouse middle button will still be appreciated.

Jay

---

### Post by orb9220 on 2007-06-22
> Not sure why Orb9229 already had the gui in his system tools and I did not. Hummm.


Because I used Envy to install and configure my nvidia which also puts the nvidia-settings there.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by PHuN on 2007-08-14
I was having an issue too and found this thread a hop skip away.
Worked for me, hope it helps you.
[http://ubuntuforums.org/showthread.php?t=230293]("http://ubuntuforums.org/showthread.php?t=230293")

-phun-

---

### Post by mukiex on 2007-10-27
For the sake of minimizing link hoppage (the code takes up so little space, why require another jump?), the solution from that page :

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "5"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Emulate3Buttons" "true"
EndSection

```

Worked for my wireless click. =3 (well, I set my button6 to show widgets in compiz, YMMV)

---

### Post by joop905 on 2007-10-27
Then, you will modify your /etc/X11/xorg.conf (or XF86Config-4) file to register that your mouse is more than the "standard" five (5) button mouse.



Another Example - Logitech 510

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "Buttons" "7"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "ButtonMapping" "1 2 3 6 7"
        Option      "Resolution" "800"
EndSection

---

