---
title: "No fans on macbook pro 5.4 with Ubuntu 12.04"
date: 2012-08-10
forum: Apple Hardware Users
---

### Post by nimades on 2012-08-10
Hi guys,

I've just installed Ubuntu 12.04 on my Macbook pro 5.4 and its all going great. Except the fans. They don't appear to be working.

Naturally this is a bit of a problem, what with overheating and all that. I'm getting by with my cooling pad for now, but this isn't a long term solution. I've had a look through the forums but nothing has been that relevant so far and the one I have tried didn't work. 

So basically, does anyone know how I can kick start the fans?

Cheers! (P.s. sorry if this is common thing, I just haven't found anything so far!)

---

### Post by sgarman on 2012-08-10
Is the applesmc kernel module loaded? (lsmod | grep applesmc)

If not, that's the first problem you'll need to resolve.

Second - are you using macfanctld? You can get that from the mactel-support ppa repository.

Scott

---

### Post by nimades on 2012-08-11
Yeah sorry, I'm really new at this. How do you tell if the applesmc kernel module is loaded? Been searching for the answer for ages and can't find anything...

---

### Post by sgarman on 2012-08-11
In a terminal window, type

```
lsmod | grep applesmc
```

If that command returns nothing, the module is not loaded. In that case, try:

```
sudo modprobe applesmc
```

If that command hangs for a while before returning you to the command prompt, it no doubt means there were problems loading the driver. The **dmesg** command will show you output from the kernel, and you should see some errors related to the applesmc driver.

So to add the mactel-support ppa to your package manager, you would do the following:

```
sudo add-apt-repository ppa:mactel-support/ppa
sudo apt-get update
sudo apt-get install applesmc
```

Now you can try modprobe'ing the applesmc module and it should work.

Step 2 is getting the macfanctld daemon installed. That too is in the mactel-support ppa, so assuming you have already added the repository as above, you'd just:

```
sudo apt-get install macfanctld
```

Then you can start the daemon with:

```
sudo service macfanctld start
```

Take a look at **/etc/macfanctld.conf** to change the configuration if needed - on some systems you may need to tell macfanctld to ignore certain sensors output.

Finally, to monitor your actual fan speeds, you can keep a terminal window open with the following command running:

```
watch sensors
```

That will run the sensors command every 2 seconds, showing you temperature readings from your CPU as well as the fan speeds. Just hit Ctrl-C to exit from the watch command. 

Scott

---

### Post by terryeden on 2012-08-25
Sorry to hijack this thread - any idea how I increase the minimum fan speed?
At 2000, it's just a little too warm for me.

---

### Post by philcolbourn on 2012-09-01
Try editing your /etc/macfanctld.conf file.

---

