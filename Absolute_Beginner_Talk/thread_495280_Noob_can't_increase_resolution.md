---
title: "Noob can't increase resolution"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by iUSER-Mike on 2007-07-07
Hi all, I can't figure out how to change resolution. Got a Voodoo fx 3 card and an ATI rage pro turbo agp card (sat on the side). Which is the better card and how do I get 1024 x 768 resolution, please.

Cheers 

Mike:D

---

### Post by Qwerty_ on 2007-07-07
Can you not set it from System>Preferences>Screen Resolution?

---

### Post by iUSER-Mike on 2007-07-07
Hello Qwerty,

No, all I get is 800 by 600 or 640 by 480. Thats no good.:)
Cheers Mike

---

### Post by Wiebelhaus on 2007-07-07
```
sudo dpkg-reconfigure xserver-xorg -p high
```

Select the resolutions you want with the space bar then save by hitting enter with the "OK" highlighted , the restart , that'll get ya fixed up man.

---

### Post by Qwerty_ on 2007-07-07
I remeber having this very same problem about this time last year.

```
sudo dpkg-reconfigure xserver-xorg
```

solved it for me.

---

### Post by Wiebelhaus on 2007-07-07
Oh yea , also first you can try enabling desktop effects and letting it install the restricted driver , then restart , that might do it , if not go with my first suggestion.

---

### Post by Vendetta_NZ on 2007-07-07
I just installed the Nvidia Drivers, I think its

```
sudo apt-get install nvidia
```

Then

```
sudo dpkg-reconfigure xserver-xorg
```

Reconfigure your x-org file to include the required resolution and thats it :)
When you're done fixing the x-org.conf file, then press Ctrl+Alt+Backspace to restart XServer, and your resolution should be 1024x768 or whatever you wanted it to be.
You will need to go into Screen Resolution under System -> Preferences and make it the default resolution to prevent to going back to the default resolution on restart.

---

### Post by Qwerty_ on 2007-07-07
> **sx66gns said:**
> Oh yea , also first you can try enabling desktop effects and letting it install the restricted driver , then restart , that might do it , if not go with my first suggestion.

System>Administration>Restricted Drivers

Will also get you there.

---

### Post by iUSER-Mike on 2007-07-07
Hello, Desktop effects won't enable. Also what is 

    sudo dpkg-reconfigure xserver-xorg           ??

Cheers mike:)

---

### Post by Qwerty_ on 2007-07-07
> **iUSER-Mike said:**
> Hello, Desktop effects won't enable. Also what is 

    sudo dpkg-reconfigure xserver-xorg           ??

Cheers mike:)

It will let you reconfigure your xserver (what is used to display the stuff you see) so you can set it to run at the resolutions you want.

---

### Post by iUSER-Mike on 2007-07-07
Sorry, I mean, is it like a Command Prompt in Windows?

Cheers mike:)

---

### Post by Qwerty_ on 2007-07-07
Oh right you type that into a terminal.

Applications>Accessories>Treminal.

So yeah like a windows command prompt command. If that makes sense.

---

### Post by iUSER-Mike on 2007-07-07
Hi Qwerty, I type in the code, hit enter. It replies with Password and I can't type anything in??????????
Mike

---

### Post by Qwerty_ on 2007-07-07
It is a security feature. You cant see what you are typing, which prevents people from stealing your password.

I was just thinking and I wonder if you should install some drivers. I am not sure as to what you would install though.

---

### Post by iUSER-Mike on 2007-07-07
Could this take long? Its 2.26 am here, and I'm struggling to keep awake. Maybe I need to sleep and try again later.

Hope to catch you later. Thanks for helping. 

Cheers Mike:D

---

### Post by iUSER-Mike on 2007-07-08
Hello Everyone,  I'm back trying to sort my resolution.

sudo dpkg-reconfigure xserver-xorg -p high  Having typed this into the Terminal, I was asked to choose a manufacturer, and chose Voodoo and set my 1024 by 768 size and pressed enter. Went back to Screen Resolution but the settings are still the same. Do I need to find a driver, as Qwerty suggested?

Cheers Mike:confused:

---

### Post by iUSER-Mike on 2007-07-08
Hellooooo!

Somebody please help me with my Voodoo 3 card.

Mike](*,)

---

### Post by Qwerty_ on 2007-07-08
Try going to Cntrl+alt+backspace now. That will reset the x server perhaps enabling the options.

---

### Post by iUSER-Mike on 2007-07-08
G'Day Qwerty, How are you? Do you mean right now or go back into the terminal window? I did it now and its the same.

Cheers Mike:)

---

### Post by iUSER-Mike on 2007-07-08
Doh, even if you change the card it don't like it. I also plugged in my ATI card and it wouldn't boot. It said the card was changed and somthing else, then prompted me to press enter and nothing happened. So I'm stuck with the voodoo3

Mike
:confused:

---

### Post by Qwerty_ on 2007-07-08
Mike I think I found what your looking for.

[https://help.ubuntu.com/community/Voodoo3doesnotdo3d?highlight=%28voodoo%29%7C%283%29](https://help.ubuntu.com/community/Voodoo3doesnotdo3d?highlight=%28voodoo%29%7C%283%29)

I think if you follow that through you might beable to get your resolution setup.

---

### Post by kcirtap on 2007-07-08
I have a ASUS card but the following line sudo dpkg-reconfigure xserver-xorg -p high does not change anything. I changed to 1280x768 and now my keyboard layout has changed.

edit: I also want to change to a higher resolution.

---

### Post by iUSER-Mike on 2007-07-08
Hi Qwerty,

I just stuck the ATI in and did a reinstall. Problem solved.
Thanks Mate. 
kcirtap, hope you get sorted.
Now, if only I could network to Vista......

Cheers Mike:popcorn:

---

### Post by bigtoepfer on 2007-07-08
I think what he meant by what is.....

> **iUSER-Mike said:**
> Hello, Desktop effects won't enable. Also what is 

    sudo dpkg-reconfigure xserver-xorg           ??

Cheers mike:)


i don't think he knows how to enter that in command i had to have it explained to me last night.  And i'm posting for the first time so i'm still slightly lost myself.  I got my geforce 8500 working but can't explain to someone else.  :(

---

### Post by bigtoepfer on 2007-07-08
lol, nvm guess i was a little late on that.  gratz on the fix tho

---

### Post by iUSER-Mike on 2007-07-08
Me thinks we should ask the clever users, if they could build a STICKY on graphics-cards and the various issues. The reason being, maybe a lot of us have old fossils like Pentium 2's etc, that make ideal machines to put Ubuntu on.

So, what do you think?:guitar:

Cheers Mike

---

