---
title: "won't come out of hibernation"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by KnowNothing on 2007-06-07
When I try to wake my computer up from hibernation I just get a blank screen.  It worked fine the first few times but never since.  What am I doing wrong?  What else do you need to know to help?

Thanks very much.

---

### Post by Inxsible on 2007-06-07
have you made any changes to your hibernation acpi files ?
have you installed uswsusp for suspend and hibernation ?

---

### Post by KnowNothing on 2007-06-07
No, I have not.  Should I install uswsusp?  How would I do that?

Thanks very much.

---

### Post by Inxsible on 2007-06-07
Well, yeah the built-in hibernate and suspend work only a few times for many ppl. 
It can be rectified by installing uswsusp
Check this link out
[http://ubuntuforums.org/showthread.php?t=194426&page=2](http://ubuntuforums.org/showthread.php?t=194426&page=2)
 
See post #19 which details what to do.

---

### Post by Inxsible on 2007-06-07
[SIZE=2]Unfortunately, for me even tho my machine does hibernate and suspend now, I still can't resume. But this, it seems is the problem only with my machine as many other ppl have got it working perfectly.[/SIZE]

---

### Post by KnowNothing on 2007-06-07
Thanks for the link.  Unfortunately, I'd have better luck reading ancient Greek than trying to make sense of that.  I think I'm starting to miss Windows, as much as I hated it.

Thanks again.

---

### Post by Crafty Kisses on 2007-06-07
> **KnowNothing said:**
> When I try to wake my computer up from hibernation I just get a blank screen.  It worked fine the first few times but never since.  What am I doing wrong?  What else do you need to know to help?

Thanks very much.

You can see if this works: 
```
Ctrl+Alt+F2
```

---

### Post by Inxsible on 2007-06-07
> **KnowNothing said:**
> Thanks for the link. Unfortunately, I'd have better luck reading ancient Greek than trying to make sense of that. I think I'm starting to miss Windows, as much as I hated it.
 
Thanks again.
 
Dont be disheartened. Let me list down the steps
Open up a terminal (Applications --> Accessories --> Terminal)
then type in
```
 
sudo aptitude install uswsusp

``` After that type in this command ```
gksudo gedit /etc/acpi/hibernate.sh
```
Then in the file that opens up look for a section that looks like this:
```
 
if [ -x /sbin/s2disk ]; then
DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
if [ -f /etc/usplash.conf ]; then
. /etc/usplash.conf
/sbin/s2disk -x "$xres" -y "$yres" $DEVICE
else
/sbin/s2disk $DEVICE
fi
else
echo -n "disk" >/sys/power/state
fi
 

```Change that to 
```
 
if [ -x /sbin/s2disk ]; then
/sbin/s2disk
else
echo -n "disk" >/sys/power/state
fi

```
Save and close the file.

---

### Post by Inxsible on 2007-06-07
After you have done the above go to the terminal again and type in
```
 
gksudo gedit /etc/acpi/sleep.sh

```
Once the file opens up, look for a code snippet that looks like
```
 
echo -n $ACPI_SLEEP_MODE >/sys/power/state
 

```Change that to 
```
 
if [ -x /sbin/s2ram ]; then
/sbin/s2ram -f
else
echo -n $ACPI_SLEEP_MODE >/sys/power/state
fi
 

```
 
Save the file and close. Once you have done whats listed in both my posts, your suspend and hibernate should work.

---

### Post by KnowNothing on 2007-06-07
> **Codename said:**
> You can see if this works: 
```
Ctrl+Alt+F2
```

That just turned my whole screen into a terminal.  I had to shut off the computer and turn it back on.

---

### Post by KnowNothing on 2007-06-07
I did what you instructed for hibernate.sh and then I opened suspend.sh and it is totally blank -- not a single character in there.  Would you mind posting what the entire content should be?  I really appreciate all of your help.

Thanks again.

---

### Post by Inxsible on 2007-06-07
> **KnowNothing said:**
> I did what you instructed for hibernate.sh and then I opened suspend.sh and it is totally blank -- not a single character in there. Would you mind posting what the entire content should be? I really appreciate all of your help.
 
Thanks again.
Are you sure you ran the commands exactly. Did you by chance forget the / before etc ?

---

### Post by Inxsible on 2007-06-07
Whoops you put in suspend.sh....it should be sleep.sh

---

### Post by KnowNothing on 2007-06-07
Oops, sorry about that.  I just edited sleep.sh as instructed but it still won't come out of hibernation.  I get the Ubuntu logo and one orange bar underneath.  Then it goes to a blank screen and just stays that way.  Any other ideas?

Thanks very, very much for your patience.

---

### Post by KnowNothing on 2007-06-07
Anyone ever had this problem and fixed it?

Thanks.

---

### Post by ym4546 on 2007-06-13
I'm having the same problem as KnowNothing. I tried the fix mentioned (replacing the lines in hibernate.sh and sleep.sh), however, the same problem persists. I'm wondering if it is either something to do with the fact that my comp is a dual boot or if there is a bios problem (I'm scared of flashing an updated bios, personally).

Any ideas would be appreciated.

---

### Post by cmendoza on 2007-06-14
My case is similar, i can suspend but when i try to hibernate my laptop never turns off but the screen goes blank, I waited for more than a minute but it stays the same way, so i have to turn it off by holding the power button :(

My laptop is a HP Pavilion dv6000t, dual-booting

Any help would be appreciated. Thanks in advance.

---

