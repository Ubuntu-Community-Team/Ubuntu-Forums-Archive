---
title: "Two-finger tap to middle-click on Eee PC 1000HA with Ubuntu 11.04?"
date: 2011-07-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by fullerenedream on 2011-07-08
Is it possible to get two-finger tap to mean middle-click on my Eee PC 1000HA with Ubuntu 11.04? I'm dual-booting with WinXP, which has two-finger tap to middle-click, so it would be super nice to have the same thing on my fancy new Ubuntu partition. Two-finger scrolling is enabled, so I feel like I ought to be able to get two-finger tap working, but I don't know how.

---

### Post by alelr36 on 2011-07-11
Hello!

first of all, I don't speak english perfectly...
second, yes it is possible. I have an asus K52JC and I have been using ubuntu for a few days.
I will explain the steps I have followed to make the two-fingers-clic generate a scroll-clic (for opening new tabs for example), and the three-fingers-clic a right-clic...

1) Open a new terminal
2) Type ```
sudo su
```, and write the pass

(I think steps 1 and 2 are optional but I'm not sure)

3) Type ```
xinput list
```
From the list you have to locate the Touchpad, in my case *ETPS/2 Elantech Touchpad*. See the id of this device.

4) Type ```
xinput list-props id_of_touchpad
```
You will see a list of properties, look for *"Tap Action"*, and see the id of this prop (the number between () nex to *"Tap Action"*)

5) Now you have the device's ID and the clic-prop ID. What you have to do is to set a new group of parameters to this prop. Type ```
xinput set-prop id_of_touchpad id_of_property 0 0 0 0 1 2 3
```

6) It's done.

The parameters 0 0 0 0 1 2 3, describe de following actions:

(all the zeros) tap in the corners of the touchpad, I don't remember the exact order but, 0 = no response.

The 1, makes a clic, and it is in the fifth place be cause that place represents the single touch on the touchpad.

The 2, makes a scroll clic, and it is in the sixth place be cause that place represents the two-fingers clic.

the 3, I supose you are guessing, is the right clic, and the last place is for the three-fingers clic.

you should make a text file whith the line 
 ```
xinput set-prop id_of_touchpad id_of_property 0 0 0 0 1 2 3
```

save it as file.sh, or any name you like but as an .sh

and add it to the start apps, put the .sh file in somewhere where you will findit, some times when I wake up the machine, I have to configure it again...

I hope you will fix it

---

