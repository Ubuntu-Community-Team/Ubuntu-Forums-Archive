---
title: "Cannot import photos from camera"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-03-11
Hi am not able to import photos from my camera. From the time I tried a few weeks ago it identified the camera with the wrong model number but i was able to import pic's so I didn't worry about it. In the last week it won't import and says it doesn't see the camera.  Is there something I did wrong?

---

### Post by Sef on 2007-03-11
1) What are you computer system specs?

2) What camera are you using?

---

### Post by rapattack1 on 2007-03-11
I have an AMD xp2000(runs at 1.6gig), 704mb ram, 40gig hd. Not sure what other info you need. The camera is an Olympus D-535 and the system sees it as another model number.

---

### Post by rko618 on 2007-03-13
> **rapattack1 said:**
> I have an AMD xp2000(runs at 1.6gig), 704mb ram, 40gig hd. Not sure what other info you need. The camera is an Olympus D-535 and the system sees it as another model number.

What happens when you try to import? If you get this error: 
> An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

Then check:
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)
if that doesn't work then try
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146)

---

### Post by rapattack1 on 2007-03-13
Here is a screenshot of what is happening.

---

### Post by pearlie on 2007-03-13
Thanks very much, rko618!  The first bugfix - editing libgphoto2 udev rules - worked dandy for me (x64 6.10, Canon A95 camera).  :mrgreen:

---

### Post by davesmith on 2007-03-13
i have exactly this problem and the same error message with a Fuji FinePix Zoom F30
rko618

I tried bugfix 91250, but I cant save the 45-libgphoto2.rules file. It gives an error message that it&#347; a read only file, and I dont have permission to save it.

How do I change and then save the file? Any help appreciated

Davesmith

---

### Post by bedfojo on 2007-03-13
You need to edit the file as root.

Try starting gedit with "sudo gedit" which should allow you to save the file.

---

### Post by jamere on 2007-03-13
rko...THANKS!!! I repeat what pearlie said...worked for me also! I have an HP Photosmart 318 digicam. :lolflag:

---

### Post by davesmith on 2007-03-13
bedfojo

I thank you most kindly, i did save the file using gedit, the bugfix worked and now i can import my pics:) 

It was a Fuji Finepix Zoom F30

Davesmith

---

### Post by rapattack1 on 2007-03-14
How do I get to that file to edit it? I am still dealing with this problem if what is said above is relevent to me?????

---

### Post by nflynn2k7 on 2007-03-15
what do i go into to change these things

---

### Post by jamere on 2007-03-15
see the links posted by rko618 above. the first link fixed my problem. I had to go into Terminal and edit module noted below (changed line 3 as suggested):

> Binary package hint: libgphoto2-2

The file /etc/udev/rules.d/45-libgphoto2.rules says in line 3:

BUS!="usb*", GOTO="libgphoto2_rules_end"

while recenly updated udev doesn't produce BUS properties in corresponding event. Thus this line makes the whole file useless, because BUS!="usb*" is never true.

Something like

SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

instead would work.


Hope this helps...worked for me! jim

---

### Post by nflynn2k7 on 2007-03-15
what do i type to edit could you go step by step please

---

### Post by Drakkor on 2007-03-15
Yep, follow rko's instructions, it just worked on mine !!  Finally,lol  :) 
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)
You have to be root to edit the file.

---

### Post by Drakkor on 2007-03-15
Do either of you have automatix2 installed ? with scripts, it's easy to be root to edit a file,
I'm sure there's other ways, but that's the way I do it. It's located in Places>Computer>
Filesystem...  etc//udev/rules.d/45-libgphoto2.rules. Good luck !! :)

---

### Post by nflynn2k7 on 2007-03-15
please can someone take me though this step by step

---

### Post by silkstone on 2007-03-15
Many thanks for this info. I couldn't get direct import either (from a Canon 30D) but it works fine after editing 45-libgphoto2.rules as suggested.

---

### Post by nflynn2k7 on 2007-03-15
please post step by step what you did

---

### Post by nflynn2k7 on 2007-03-15
works now thanks

---

### Post by silkstone on 2007-03-15
1. Start the terminal.

2, Type in: **sudo gedit /etc/udev/rules.d/45-libgphoto2.rules**

3. You will be asked for your password. Enter it carefully - it will not appear on the screen.

4. You will then see a new window with the file 45-libgphoto2.rules displayed.

5. Look at the third line. It probably reads: BUS!="usb*",GOTO="libgphoto2_rules_end"

6. Edit that line to read: **SUBSYSTEM!="usb_device",GOTO="libgphoto2_rules_end"**
 (Note that only the part before GOTO changes.)

7. Save the file.

8. Type EXIT and hit Return to leave the terminal.

(Not sure if you have to reboot for this to take effect ??? )

---

### Post by rko618 on 2007-03-15
> **silkstone said:**
> 1. Start the terminal.

2, Type in: **sudo gedit /etc/udev/rules.d/45-libgphoto2.rules**

3. You will be asked for your password. Enter it carefully - it will not appear on the screen.

4. You will then see a new window with the file 45-libgphoto2.rules displayed.

5. Look at the third line. It probably reads: BUS!="usb*",GOTO="libgphoto2_rules_end"

6. Edit that line to read: **SUBSYSTEM!="usb_device",GOTO="libgphoto2_rules_end"**
 (Note that only the part before GOTO changes.)

7. Save the file.

8. Type EXIT and hit Return to leave the terminal.

(Not sure if you have to reboot for this to take effect ??? )

Thank you for posted the step-by-step.  I had no idea that so many people were also having this problem.  I am amazed that the fix had not been posted on these forums previously.

and no, you don't have to reboot for it to take effect.

---

### Post by Drakkor on 2007-03-16
yeah,rko, udaman !,lol :KS 
This is just another reason to just quit Xp, all the way, .......... :) 
now if there was just a way for me to play Halo, I would quit my dual boot and be all
UBUNTU !!   Don't like VM, wine, or Cedega !!

---

### Post by yabbadabbadont on 2007-03-16
> **rko618 said:**
> I am amazed that the fix had not been posted on these forums previously.

It has been, many times...  people just don't seem to know how to search properly.  :D

---

### Post by rko618 on 2007-03-16
> **nflynn2k7 said:**
> what do i go into to change these things

nflynn2k7 can you please be more specific?  The steps needed to fix this issue have been given in great detail.  What is it that you don't understand.  Please read the whole thread and then if you still don't understand post a sensible question.

---

### Post by nflynn2k7 on 2007-03-16
> **rko618 said:**
> nflynn2k7 can you please be more specific?  The steps needed to fix this issue have been given in great detail.  What is it that you don't understand.  Please read the whole thread and then if you still don't understand post a sensible question.

before this page 3 i posted that i have fixed it now, thanks for everyones help

---

### Post by rapattack1 on 2007-03-16
Thanks Silkstone I did as instructed but that file was empty. No text at all. I entered that line anyway but now there is no reaction from the system at all. Nothing pops up when I plug in the camera. Admittedly I haven't rebooted so we'll see but maybe there is supposed to be more in it.

---

### Post by Drakkor on 2007-03-16
Here's my text file from libgphoto2, you might try this, I have to make two posts because it's too many characters for one, I don't know if it'll work for you,
just copy the whole thing, and paste it into the empty text file, good luck  :) 

# udev rules file for libgphoto2 devices (udev < 0.98)
#
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"
ACTION!="add", GOTO="libgphoto2_rules_end"

SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="06bd", SYSFS{idProduct}=="0403", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="06bd", SYSFS{idProduct}=="0404", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04fc", SYSFS{idProduct}=="504b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04fc", SYSFS{idProduct}=="504a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="08ca", SYSFS{idProduct}=="0111", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04fc", SYSFS{idProduct}=="504a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04fc", SYSFS{idProduct}=="504b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0e79", SYSFS{idProduct}=="120a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="093a", SYSFS{idProduct}=="010f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="093a", SYSFS{idProduct}=="010f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="913c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0919", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="093a", SYSFS{idProduct}=="010f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a5", SYSFS{idProduct}=="3003", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3047", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30c0", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="304d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3066", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30bf", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3075", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3075", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30ba", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30ba", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30c1", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="310e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b4", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b4", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30ff", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="311c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30fe", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30f2", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3116", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3119", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3136", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="309b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="309b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30c4", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3072", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3072", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b6", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b6", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3052", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3065", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3070", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3071", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30f1", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="306a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3088", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3087", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3083", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30ea", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30ec", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3084", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3099", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3113", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30ef", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30ee", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3110", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3101", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3044", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3060", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3084", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3099", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3084", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3099", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="308e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3046", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="304b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30ba", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b4", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30c1", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30c4", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="306b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3096", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="307c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="307a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3096", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="308e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3082", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3081", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3080", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30a9", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="306b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3082", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3081", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="307f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3080", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="306b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3096", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30a9", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3105", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="308e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="304f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3061", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="304e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3062", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3059", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3076", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3076", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b8", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b8", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3058", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b7", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b7", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30f9", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30f8", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30c2", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30c2", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30c1", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3126", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="311b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3074", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3074", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30fd", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30fc", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="313a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3139", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3073", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3073", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3117", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3138", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b5", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b5", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="309a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="309a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b9", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b9", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30bb", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30bb", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3048", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3055", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="306e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="306f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3085", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3085", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b3", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b3", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3125", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="309b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3049", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="309c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3041", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3045", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3051", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30f0", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3043", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3065", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3070", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3071", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="311a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3057", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="304c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3066", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3056", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3075", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30ba", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30ba", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="306c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="306d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3077", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3077", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b4", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b4", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b2", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b2", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b1", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b1", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30fa", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="309b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3072", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3072", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b6", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30b6", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30c4", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30c0", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30c1", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30f1", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30ff", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30f2", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="311c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="30fe", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3119", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3050", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="305c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3078", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07cf", SYSFS{idProduct}=="1042", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="055f", SYSFS{idProduct}=="c200", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="905c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="1002", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0797", SYSFS{idProduct}=="8001", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d96", SYSFS{idProduct}=="4100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03e8", SYSFS{idProduct}=="2182", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03e8", SYSFS{idProduct}=="2180", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0919", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4007", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="400a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4012", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="400b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4013", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4123", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4130", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="413c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4137", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="413d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4131", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4150", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4152", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="411f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4151", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4153", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="413e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4128", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="084d", SYSFS{idProduct}=="0003", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d64", SYSFS{idProduct}=="1021", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="905c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0c45", SYSFS{idProduct}=="8000", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="4500", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4132", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="905c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="093a", SYSFS{idProduct}=="010e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05da", SYSFS{idProduct}=="1018", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0919", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="1183", SYSFS{idProduct}=="0001", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05da", SYSFS{idProduct}=="1020", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="10d6", SYSFS{idProduct}=="2200", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="10d6", SYSFS{idProduct}=="2200", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="093a", SYSFS{idProduct}=="010e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="093a", SYSFS{idProduct}=="010f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0403", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0402", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0dca", SYSFS{idProduct}=="0002", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0dca", SYSFS{idProduct}=="0002", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04cb", SYSFS{idProduct}=="014a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04cb", SYSFS{idProduct}=="0193", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04cb", SYSFS{idProduct}=="019b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04cb", SYSFS{idProduct}=="0142", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0919", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0919", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0797", SYSFS{idProduct}=="801c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="093a", SYSFS{idProduct}=="010e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="6502", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="6202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="7c02", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="7d02", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="6302", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="6602", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="7402", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="7802", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="7202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="6e02", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="7902", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="6d02", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="6302", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="4102", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="6802", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="7102", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="6b02", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="6402", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="7602", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="6702", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="6c02", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="6a02", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="4202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="7702", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="7e02", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="4302", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="4102", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="4402", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="4502", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="4102", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="6002", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="8b02", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="7502", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="7b02", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="7302", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="7a02", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="8002", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="8102", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="8202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="8402", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="8502", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="8702", MODE="0660", GROUP="plugdev"

---

### Post by Drakkor on 2007-03-16
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9153", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="093a", SYSFS{idProduct}=="010e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="045e", SYSFS{idProduct}=="00c9", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="8086", SYSFS{idProduct}=="0630", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="112a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="2102", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="2101", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="1006", SYSFS{idProduct}=="4003", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="1006", SYSFS{idProduct}=="4002", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1117", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1113", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1118", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1114", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1119", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1116", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0784", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d96", SYSFS{idProduct}=="3300", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d96", SYSFS{idProduct}=="4100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05da", SYSFS{idProduct}=="1006", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d96", SYSFS{idProduct}=="0000", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04f1", SYSFS{idProduct}=="6105", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="084e", SYSFS{idProduct}=="0001", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="057e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="058a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="058c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="058d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0589", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="059a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="05a2", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="05ba", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="05a7", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="059c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0560", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0560", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0535", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0566", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0566", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0574", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0573", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0571", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0584", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0579", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0578", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0578", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="057a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="057b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0586", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="057c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0121", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0110", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0111", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0130", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0112", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0132", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0160", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0131", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0525", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0500", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0510", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0530", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0170", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0555", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0576", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0550", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0570", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0572", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0575", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="057d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="057f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0577", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0300", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0540", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0568", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0569", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0565", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0567", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0400", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0592", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="058e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="058f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="059d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="059e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0587", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0580", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0588", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0403", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04c8", SYSFS{idProduct}=="0722", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="132b", SYSFS{idProduct}=="0001", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="132b", SYSFS{idProduct}=="0007", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="132b", SYSFS{idProduct}=="0018", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="132b", SYSFS{idProduct}=="0022", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04da", SYSFS{idProduct}=="2375", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="1004", SYSFS{idProduct}=="6005", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d96", SYSFS{idProduct}=="4100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="046d", SYSFS{idProduct}=="0900", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="046d", SYSFS{idProduct}=="0950", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d96", SYSFS{idProduct}=="4100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d96", SYSFS{idProduct}=="3300", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04fc", SYSFS{idProduct}=="504b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0919", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04fc", SYSFS{idProduct}=="504a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d96", SYSFS{idProduct}=="4100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="2205", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d96", SYSFS{idProduct}=="4102", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="045e", SYSFS{idProduct}=="0710", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="084d", SYSFS{idProduct}=="0003", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0000", SYSFS{idProduct}=="0000", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="055f", SYSFS{idProduct}=="c200", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="055f", SYSFS{idProduct}=="a350", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="055f", SYSFS{idProduct}=="c220", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="055f", SYSFS{idProduct}=="c420", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="055f", SYSFS{idProduct}=="c520", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="905c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0302", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0117", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0116", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0122", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0109", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0108", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0115", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0121", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0111", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0110", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="011d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="012d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0204", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="010f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="010e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="010b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0130", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0131", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0129", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0113", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0206", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0119", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="012e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="010d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0135", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0103", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0112", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0102", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0104", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0208", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="041a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0305", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0140", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0142", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="014e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0401", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0404", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0408", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="040a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0402", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0410", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0406", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="040e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04b0", SYSFS{idProduct}=="0412", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04fc", SYSFS{idProduct}=="504a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0105", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0105", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0105", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0114", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0114", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0109", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0105", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0105", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0114", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0114", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0105", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0105", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0105", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0109", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0114", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0114", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0114", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0113", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0114", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0114", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="07b4", SYSFS{idProduct}=="0109", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0919", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0919", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04da", SYSFS{idProduct}=="2374", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04da", SYSFS{idProduct}=="2372", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04da", SYSFS{idProduct}=="2372", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04da", SYSFS{idProduct}=="2374", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04da", SYSFS{idProduct}=="2372", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04da", SYSFS{idProduct}=="2372", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0a17", SYSFS{idProduct}=="0009", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0a17", SYSFS{idProduct}=="000d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0a17", SYSFS{idProduct}=="0007", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0471", SYSFS{idProduct}=="014c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0471", SYSFS{idProduct}=="01eb", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0471", SYSFS{idProduct}=="014b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0471", SYSFS{idProduct}=="0165", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="093a", SYSFS{idProduct}=="010e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0784", SYSFS{idProduct}=="2888", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0546", SYSFS{idProduct}=="0daf", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="905c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="093a", SYSFS{idProduct}=="010f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0784", SYSFS{idProduct}=="5300", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04fc", SYSFS{idProduct}=="ffff", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0dca", SYSFS{idProduct}=="0004", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0784", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="220b", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="2203", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="2204", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="2208", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="220c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="0325", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="2214", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="032d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="220d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="2212", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="2213", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="2216", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="032f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="2217", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="2202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="220d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="220f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="220f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="093a", SYSFS{idProduct}=="010f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0c45", SYSFS{idProduct}=="8003", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="507f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="502e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="502f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="5a0f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="5057", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="505a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="5047", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="5054", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0781", SYSFS{idProduct}=="7410", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0781", SYSFS{idProduct}=="7420", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0781", SYSFS{idProduct}=="7420", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0781", SYSFS{idProduct}=="7400", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0474", SYSFS{idProduct}=="0230", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0797", SYSFS{idProduct}=="8901", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0797", SYSFS{idProduct}=="8909", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0797", SYSFS{idProduct}=="8911", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="084d", SYSFS{idProduct}=="1001", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0919", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="05ca", SYSFS{idProduct}=="220e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="412f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0c77", SYSFS{idProduct}=="1011", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0c77", SYSFS{idProduct}=="1015", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0c77", SYSFS{idProduct}=="1002", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0c77", SYSFS{idProduct}=="1010", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d64", SYSFS{idProduct}=="1001", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0c77", SYSFS{idProduct}=="1001", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="18f6", SYSFS{idProduct}=="0102", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d96", SYSFS{idProduct}=="3300", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0dca", SYSFS{idProduct}=="0002", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0ec7", SYSFS{idProduct}=="1008", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="004e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="905c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0919", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0919", SYSFS{idProduct}=="0100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0930", SYSFS{idProduct}=="000c", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0930", SYSFS{idProduct}=="0009", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0930", SYSFS{idProduct}=="0011", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0930", SYSFS{idProduct}=="0010", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="1132", SYSFS{idProduct}=="4337", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="1132", SYSFS{idProduct}=="4332", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="1132", SYSFS{idProduct}=="4335", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="1132", SYSFS{idProduct}=="4334", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d96", SYSFS{idProduct}=="3300", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d96", SYSFS{idProduct}=="4100", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="084d", SYSFS{idProduct}=="0003", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="06d6", SYSFS{idProduct}=="002e", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="06d6", SYSFS{idProduct}=="002d", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04fc", SYSFS{idProduct}=="504a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0797", SYSFS{idProduct}=="801a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0d64", SYSFS{idProduct}=="1001", MODE="0660", GROUP="plugdev"
PROGRAM="check_ptp_camera 06/01/01", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="9120", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="093a", SYSFS{idProduct}=="010f", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="0c45", SYSFS{idProduct}=="800a", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="2770", SYSFS{idProduct}=="905c", MODE="0660", GROUP="plugdev"

LABEL="libgphoto2_rules_end"

---

### Post by rapattack1 on 2007-03-16
Sorry to report it didn't work. It is back to the same error as in the beginning.

---

### Post by rko618 on 2007-03-17
LOL Drakkor in the future might I recommend adding the file as an attachment to your post instead of posting the entire thing ;-)

---

### Post by Drakkor on 2007-03-17
Yeah,cool,but I still feel I couldn't help rapattack1, sorry dude ,someone else has to solve this ! :confused:

---

### Post by freebird54 on 2007-03-17
Just a passing thought - as I hate to have anyone left not working!  From experience as a support guy (among other things!) I would look carefully for a typo in your edit command...

If you highlight the command as shown by dragging your mouse over it, then press <ctlr>c ,  then click in the terminal window and press <ctrl><shift>v , it will paste the correct code directly for you.  Then execute and make the edit.

If it wasn't that, I'll just eat the egg on my face and grin - but every time a file that is SUPPOSED to be there to edit seems empty - that was my problem :D

---

### Post by rapattack1 on 2007-03-17
Well sounds like this is another job for my Linux friend that comes to my place now and then. Thanks for trying guys. I am really good with the old copy paste thing so it is not that!
Will report when all is well and hopefully pick up why this happened and what the solution was.
:KS

---

### Post by leo antony on 2007-03-28
Hello all, 

I was trying to import from a Canon Ixus 330. Had the same problems as those posted here. The bug fix via the link from RKO fixed it:

replaced
BUS!="usb*", GOTO="libgphoto2_rules_end"

in
/etc/udev/rules.d/45-libgphoto2.rules

with
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

Thanks RKO!

---

### Post by leo antony on 2007-03-28
One more thing, if you're still having trouble. Try importing with your photo manager, which for me was graphics-->f-spot. I couldn't import directly when the camera was picked up.

---

### Post by rapattack1 on 2007-03-28
Yeah I did try that at some point with no success. I tried to compare information on my laptop about this situation as the camera works with the laptop and I can't see any difference. It has the same edgy ubuntu on it. I can't understand why it started misbehaving with the desktop and not the laptop.
There is a screen shot below.

---

### Post by leo antony on 2007-03-31
Surprised you're not getting a little more help. 

So, you did try to go through a photo manager? Even after the bug fix, I would still get the error message, but using a photo manager, I was able to transfer files. Maybe try fspot if you're not using it.

I'm new to all this. Please post your solution if you get one. 

Cheers,

Leo

---

### Post by rapattack1 on 2007-03-31
No sorry I wasn't able to import pic's in anyway shape or form up until 2 days ago but I may have found out why. Now the system is inaccessable so I can't test anything. I have to reinstall and maybe the right version of edgy. As of 2 days ago I booted up and the mouse is frozen so I am trying to find a way to retrieve my files. A friend said what may be the problem all along as the camera not being recognised wasn't the only problem, is that I may have the wrong version installed on the machine. It is an amd and he said that ubuntu installs the lowest version by default. Which is intel. Anyway it will take a while before I work out  how to maybe burn my files from the command line? I have never done this but it sounds efficent or install another drive with edgy on it and drag the files over from the old drive.

---

### Post by overdrank on 2007-03-31
> **rko618 said:**
> What happens when you try to import? If you get this error: 


Then check:
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)
if that doesn't work then try
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146)

Thanks the first link worked for me, HP Photosmart M425. Thanks alot guys.
:guitar:

---

