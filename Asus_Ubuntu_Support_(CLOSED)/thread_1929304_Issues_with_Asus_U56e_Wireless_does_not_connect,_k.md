---
title: "Issues with Asus U56e: Wireless does not connect, kernel stopped upgrading, runs hot"
date: 2012-02-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Ubun2 gy on 2012-02-21
Hello,

I recently purchased an Asus U56e (Intel Core i5-2410M, 6gb RAM), and the first thing I did was install Ubuntu 11.10. I have used Ubuntu on other machines for several years with varying degrees of success, and chose the U56E because it had the features I wanted and I did not find any indication that it was incompatible with Ubuntu. I currently have it triple booting along with Mint 12 and Windows 7 (eek), neither of which I really use. When I first installed, it would crash if I shut the lid or suspended it, but that I have fixed. There are three problems that I still find extremely inconvenient:

1: Wireless does not work in Ubuntu. I have tried many of the fixes suggested [here]("http://ubuntuforums.org/showthread.php?t=1862484"), with no effect. 

2: After 3.0.0-14-generic, my kernel quit upgrading. Both 3.0.0-15 and 3.0.0-16 have downloaded and installed when I upgrade, but never replaced the old one when I boot. when I type try to install 3.0.0-16 it says it is already installed and the latest version.

3: My machine runs hot, and battery life is much better in Windows. The fan runs constantly in Ubuntu, while in windows it only seems to turn on when I am doing heavy processing.

Any suggestions would be greatly appreciated.

Ubun2 gy

P.S.
I think it would be nice if Ubuntu ran a little leaner in general. Compiz crashes frequently, and boot time in 11.10 is horrible compared to 11.04. Granted, I still did beat my brothers Macbook Pro nicely (26.3 seconds to 56.x seconds ;)).

---

### Post by Ubun2 gy on 2012-03-02
Bump! :rolleyes:

---

### Post by Ubun2 gy on 2012-03-02
Today my brother and I figured out the kernel problem, but the other two problems remain unresolved. The kernel problem was that Mint is in control (don't ask me why;)) of grub, so I updated the kernel in Ubuntu and then updated grub from Mint.

---

### Post by @gu79 on 2012-03-08
I guess you installed Mint last. You can solve it reinstalling grub from ubuntu (check [this ]("http://ubuntuforums.org/showthread.php?t=1581099")for more info):

```
sudo grub-install --recheck /dev/sd[COLOR=Red]X[/COLOR]
sudo update-grub
```(replace X according to your drive, "sda" for example)

For the power issue (fans, temperature, battery life), try adding **i915.i915_enable_rc6=1** as a kernel boot parameter: in the grub menu, press "e" to edit the line of Ubuntu, and then add that to the end of the line of the kernel (starting with linux). 
For example: linux /boot/vmlinuz-3.0.0-16-generic <...> quiet splash vt.handoff=7 i915.i915_enable_rc6=1

If that works, you can modify grub to have it permanent:
```
 gksu gedit /etc/default/grub
```GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1"
And update grub, **sudo update-grub**

They are fixing some bugs to have that as default in 12.04. [Check this]("https://wiki.ubuntu.com/Kernel/PowerManagementRC6").

About the wireless, do you see any network at all?

---

### Post by WBMachinery on 2012-03-17
I had the same problem with the same computer enter these commands and it will be solved.

sudo modprobe -r iwlagn
sudo modprobe iwlagn bt_coex_active=0

If it worked you need to make it permanent.

To make the change permanent:

gsku gedit /etc/modprobe.d/iwl.conf

Copy/paste this line into the new file:
options iwlagn bt_coex_active=0

Save and quit.

After you do this you will experience very slow internet connection but it can be solved by making iwlag not use n and it can be done with these commands.

sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1

if you see it made a difference once again you must make it perminent..

gksudo gedit /etc/modprobe.d/iwlagn-disable11n.conf
options iwlagn 11n_disable=1

Save and quit. 
And thats all

---

### Post by Ubun2 gy on 2012-03-18
@gu79,
thanks for responding. Wireless networks show up fine, but when I try to connect it tries for a few minutes and then announces that it has failed and keeps on trying indefinitely.

I tried both of the fixes you mentioned. The grub update worked nicely, but RC6 garbled the top bar, lost my unity settings and made 1024 x 768 the only available screen resolution, so I think I will just wait until April 26th in case 12.04 has improved the power handling.

[WBMachinery]("http://ubuntuforums.org/member.php?u=1522272"),
I just tried what you suggested (with gksu substituted for gsku), and it seems to have worked admirably - thank you! I did not notice it being slow after the first command, but I was not doing anything very taxing so I did the second one for good measure. I am happy to say that this post was made on wireless.



Thank you both for the help,
Ubun2 gy

EDIT: My apologies for the slow reply, the power has been out for several days here (west coast of Canada), and other power outages that did not directly affect me knocked out my Internet two or three times.

---

### Post by skyeman1 on 2012-04-06
Thank you! 
The mod worked!!

But when we wanted to make the change permanent, Ubuntu did not recognize the gsku function.

We are COMPLETE Ubuntu newbies. 

Is there a way to get that function? Is it part of a downloadable and installable addition?  We're currently running 11.10 with the latest updates.

---

### Post by @gu79 on 2012-04-06
> **skyeman1 said:**
> 
But when we wanted to make the change permanent, Ubuntu did not recognize the gsku function.


That's a typo. Instead of gsku, you should use gksu, so:

gksu gedit /etc/modprobe.d/iwl.conf

"sudo" gives the instructions you are executing root (administrative) privileges, while gksu does the same, but for visual applications outside the terminal (read [sudo vs gksu]("http://ubuntu.paslah.com/sudo-and-gksu/")).

---

### Post by WBMachinery on 2012-04-26
Glad I could help! (sorry for the typo)

---

### Post by Ubun2 gy on 2012-04-27
Hello, 
Thanks for the help on these issues! 

I upgraded to 12.04 today, and my WiFi bit the dust again (even though it is a LTS...:-k). 

It did a similar thing to when I first installed 11.10; my network showed up, but it spent forever trying to connect. The only difference was that in the network connections indicator (if that is what it is called), there was a small arrow next to the network name which popped out into a long list of the network name and then a number. There were about twenty of them, and none worked.
 I tried using the edit connections to delete them, but still I cannot connect to other available networks, and my network has not show up again. 

I also tried using the commands WBMachinery suggested that worked on 11.10, before and after, but it did not work this time. 

If you have any other suggestions I would appreciate it! 
I can also provide any other info you need.

Thanks again for you time,
Ubun2 gy

---

### Post by WBMachinery on 2012-04-27
In the new kernel the wireless interface changes from iwlagn to iwlwifi, you can verify this with the command 

lspci -v

and look under Network controller on the section called kernel modules.

So all you have to do is subsitute iwlwifi in the commands I already posted instead of iwlagn and you should be good to go.

sudo modprobe -r iwlwifi

sudo modprobe iwlwifi bt_coex_active=0

gksu gedit /etc/modprobe.d/iwl.conf

options iwlwifi bt_coex_active=0

and to ensure fast internet do the same:

sudo rmmod -f iwlwifi
gksu gedit /etc/modprobe.d/iwlwifi-disable11n.conf

options iwlwifi 11n_disable=1

---

### Post by Ubun2 gy on 2012-04-27
> **WBMachinery said:**
> In the new kernel the wireless interface changes from iwlagn to iwlwifi, you can verify this with the command 

lspci -v

and look under Network controller on the section called kernel modules.

So all you have to do is subsitute iwlwifi in the commands I already posted instead of iwlagn and you should be good to go.

sudo modprobe -r iwlwifi

sudo modprobe iwlwifi bt_coex_active=0

gksu gedit /etc/modprobe.d/iwl.conf

options iwlwifi bt_coex_active=0

and to ensure fast internet do the same:

sudo rmmod -f iwlwifi
gksu gedit /etc/modprobe.d/iwlwifi-disable11n.conf

options iwlwifi 11n_disable=1

I tried these commands, and they do not seem to have any effect other than that sudo rmmod -f iwlwifi removes all wireless info from the indicator menu, as well as the option to enable wireless. The only thing that I can think of is that maybe deleting multiple versions with "edit connections" caused a problem, but I am not completely sure how to re-add my network.  
Thanks for your help, and any further suggestions would be appreciated!

---

### Post by Ubun2 gy on 2012-04-30
Bump! 8-)

---

### Post by @gu79 on 2012-05-01
> **Ubun2 gy said:**
> Bump! 8-)
If you see other networks and not yours (your SSID is not hidden, right? ;)), I guess it could be that your router is using high channels (above 10), which are not visible from ubuntu. I have had that problem and setting the router to transmit in a lower channel solved the problem. Hope it helps, otherwise I have no idea what to do...

---

### Post by WBMachinery on 2012-05-01
If you upgraded Ubuntu the old files that were changed with the commands didn't get removed and are probably conflicting the new files, try deleting them all, first find all of those files with 

ls /etc/modprobe.d | grep iw

you should see all the files that where created with the previous commands, to delete them use the command

sudo rm "name of file" 

for each file that was found. After that try the new commands again.

---

### Post by Ubun2 gy on 2012-05-02
@gu79, the SSID is not hidden, and I am not sure if the router is on a channel above 10, but I will check. 

WBMachinery, when I input ```
ls /etc/modprobe.d | grep iw
``` into terminal I get the following results: 
```
iwlagn-disable11n.conf
iwl.conf
iwl.conf~
iwlwifi-disable11n.conf
iwlwifi-disable11n.conf~
```but when I type ```
sudo rm iwlagn-disable11n.conf
```I get ```
rm: cannot remove `iwlagn-disable11n.conf': No such file or directory

```I have no clue why this is happening [-o<

---

### Post by WBMachinery on 2012-05-03
Well first of all you should delete all of those files, because they are conflicting with each other. 

Sorry that I forgot to tell you that in order to modify a file in any way you must be located in the directory that contains it. So you can either change directories or you can specify it in the command like this:

```
sudo rm /etc/modprobe.d/"name of file"
``` 

execute this command for all the files that you found, for example:

```
sudo rm /etc/modporbe.d/iwl.conf~ 
```

To ensure that all of the files were erased properly do the grep command once more and nothing should appear.
```
ls /etc/modprobe.d | grep iw
```
Then repeat the commands I have already posted with the iwlwifi change and you should be good to go.

---

### Post by Ubun2 gy on 2012-05-04
Success!
It is working now, I do not know why I did not think of cd'ing into the directory.

Thanks @gu79; it turned out that another user on the network had accidentally hidden the SSID!](*,)

My install is now (knock on wood) running smoothly, and the power managemt in 12.04 compared with 11.10 is like night and day!

---

### Post by chrisgianti on 2012-05-20
> **@gu79 said:**
> I guess you installed Mint last. You can solve it reinstalling grub from ubuntu (check [this ]("http://ubuntuforums.org/showthread.php?t=1581099")for more info):

```
sudo grub-install --recheck /dev/sd[COLOR=Red]X[/COLOR]
sudo update-grub
```(replace X according to your drive, "sda" for example)

For the power issue (fans, temperature, battery life), try adding **i915.i915_enable_rc6=1** as a kernel boot parameter: in the grub menu, press "e" to edit the line of Ubuntu, and then add that to the end of the line of the kernel (starting with linux). 
For example: linux /boot/vmlinuz-3.0.0-16-generic <...> quiet splash vt.handoff=7 i915.i915_enable_rc6=1

If that works, you can modify grub to have it permanent:
```
 gksu gedit /etc/default/grub
```GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1"
And update grub, **sudo update-grub**

They are fixing some bugs to have that as default in 12.04. [Check this]("https://wiki.ubuntu.com/Kernel/PowerManagementRC6").

About the wireless, do you see any network at all?

>>I would like to try your power solution  **i915.i915_enable_rc6=1 ... **but I have no idea how to do what you described. I also have a u56e (mine is a bal7) with similar specs as the guy who started this question (except I only have windows 7 & ubuntu 11.04 on my machine).
Could you provide more instruction for a linux newbie?

---

### Post by @gu79 on 2012-05-20
> **chrisgianti said:**
> >>Could you provide more instruction for a linux newbie?
A quick reply. Let me know if you need more help. 

Grub is the program that shows you the different options [during boot]("http://blog.sesatu.com/wp-content/uploads/grub2.jpg"). So, select the line that you usually select to boot into ubuntu, but instead of pressing enter, press "e". In the next screen, go to the line that starts with "linux/boot/vmlinuz..." and append to that line:
**i915.i915_enable_rc6=1**  
Press Ctrl-x to boot.

That's not permanent, so if something doesn't work properly, just reboot.

---

### Post by chrisgianti on 2012-06-10
> **@gu79 said:**
> A quick reply. Let me know if you need more help. 

Grub is the program that shows you the different options [during boot]("http://blog.sesatu.com/wp-content/uploads/grub2.jpg"). So, select the line that you usually select to boot into ubuntu, but instead of pressing enter, press "e". In the next screen, go to the line that starts with "linux/boot/vmlinuz..." and append to that line:
**i915.i915_enable_rc6=1**  
Press Ctrl-x to boot.

That's not permanent, so if something doesn't work properly, just reboot.

After trying this for a few weeks, I'm not sure if I'm noticing any difference. It runs warm & keyboard is warm as well. Maybe it's just supposed to be like this. The command doesn't seem to hurt anything. What is this command doing, btw? Do I need to download drivers? Model again is U56E-BAL7 asus.

Any other recommendations? Looks like I've got a lot of studying linux up ahead, which is cool. I like ubuntu & learning this, problem solving, etc.  It's been well worth all the hard work because I've been able to do things in linux that windows couldn't handle. (running 5 routers + 2 windows machines all within ubuntu)

---

### Post by @gu79 on 2012-06-11
Not a clue. A good indication should be the battery life. What about the temperature in windows?
You could try to install 12.04 and see how it behaves there. 
About RC6:
[https://wiki.ubuntu.com/Kernel/PowerManagementRC6](https://wiki.ubuntu.com/Kernel/PowerManagementRC6)

---

### Post by chrisgianti on 2012-06-12
> **@gu79 said:**
> Not a clue. A good indication should be the battery life. What about the temperature in windows?
You could try to install 12.04 and see how it behaves there. 
About RC6:
[https://wiki.ubuntu.com/Kernel/PowerManagementRC6](https://wiki.ubuntu.com/Kernel/PowerManagementRC6)


That's an awesome informational link. Thanks. This stuff is so cool.
:guitar:

---

### Post by schweet on 2012-06-14
> **WBMachinery said:**
> I had the same problem with the same computer enter these commands and it will be solved.

sudo modprobe -r iwlagn
sudo modprobe iwlagn bt_coex_active=0

If it worked you need to make it permanent.

To make the change permanent:

gsku gedit /etc/modprobe.d/iwl.conf

Copy/paste this line into the new file:
options iwlagn bt_coex_active=0

Save and quit.

After you do this you will experience very slow internet connection but it can be solved by making iwlag not use n and it can be done with these commands.

sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1

if you see it made a difference once again you must make it perminent..

gksudo gedit /etc/modprobe.d/iwlagn-disable11n.conf
options iwlagn 11n_disable=1

Save and quit. 
And thats all


The change worked, and I would like to make it permanent, but when you wrote, 

"Copy/paste this line into the new file:
options iwlagn bt_coex_active=0"

I don't know what you mean by "the new file" could someone walk me through this step?

thanks

---

### Post by REGELDUDES on 2012-08-02
[QUOTE=WBMachinery;11773925]I had the same problem with the same computer enter these commands and it will be solved.

sudo modprobe -r iwlagn
sudo modprobe iwlagn bt_coex_active=0

If it worked you need to make it permanent.

To make the change permanent:

gsku gedit /etc/modprobe.d/iwl.conf

Copy/paste this line into the new file:
options iwlagn bt_coex_active=0

Save and quit. [end quote]

We did all of this and it indicated that it had connected to the wireless, but when i disconnected the Ethernet cable and it still indicated that it had connected to the wireless SSID but had no internet access. I know it isn't a problem with the modem because it works in windows fine. Please help and thanks for your efforts!

---

### Post by bouchigo on 2012-09-22
> **WBMachinery said:**
> In the new kernel the wireless interface changes from iwlagn to iwlwifi, you can verify this with the command 

lspci -v

and look under Network controller on the section called kernel modules.

So all you have to do is subsitute iwlwifi in the commands I already posted instead of iwlagn and you should be good to go.

sudo modprobe -r iwlwifi

sudo modprobe iwlwifi bt_coex_active=0

gksu gedit /etc/modprobe.d/iwl.conf

options iwlwifi bt_coex_active=0

and to ensure fast internet do the same:

sudo rmmod -f iwlwifi
gksu gedit /etc/modprobe.d/iwlwifi-disable11n.conf

options iwlwifi 11n_disable=1

I did this, but it won't stick (not permanent).

Every time I reboot I have to use these two commands, otherwise I can't connect:

sudo modprobe -r iwlwifi

sudo modprobe iwlwifi bt_coex_active=0

There are no conflicting files in /etc/modprobe.d, I already checked that.

Any suggestions???

Thanks

---

### Post by chrisgianti on 2013-07-13
> **@gu79 said:**
> That's a typo. Instead of gsku, you should use gksu, so:

gksu gedit /etc/modprobe.d/iwl.conf

"sudo" gives the instructions you are executing root (administrative) privileges, while gksu does the same, but for visual applications outside the terminal (read [sudo vs gksu]("http://ubuntu.paslah.com/sudo-and-gksu/")).

Thanks! This worked for me (u56e-bal7, Linux Mint 15 Olivia). Took a while to find the command that worked!

---

