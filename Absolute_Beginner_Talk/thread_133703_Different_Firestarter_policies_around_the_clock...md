---
title: "Different Firestarter policies around the clock.."
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by bushtor on 2006-02-20
Hi,

How can I shut off internet (or apply another policy, with no internet access) for a range of clients during the nights from firestarter...?

Tor

---

### Post by bushtor on 2006-02-21
Too stupid question, - or not possible?

I just wondered if I can set some kind of scheduled policies (different day and night) using Firestarter.  

regards

Tor

---

### Post by 5-HT on 2006-02-21
Hi, sorry don't think that is possible to do with Firestarter (at least yet...)

Hopefully with this extra bump, someone in the know may know of another GUI firewall that can do so, or how it could be accomplished via iptables (for a new policy), or deactivating the NIC (to turn it off completely) with a script and maybe cron jobs (just a guess, don't know if that's possible either as it's beyond my needs and abilities).

HTH

---

### Post by bushtor on 2006-02-21
If Firestarter had possibilities to save a policy as a file name, then we could create different policies to be called by cron...

Tor

---

### Post by 5-HT on 2006-02-21
Hi again,

**Ok, I'd like to preface this with the explicit declaration that I have not tested this myself and do not know if it will work or if it may harm your system (I doubt it should hurt anything...just wanted to absolve myself and give warning just in case anything does).**



That being said, I'd really like to help you out.

After a little thinking, it came to mind that simple cron jobs (job scheduler) of activating/deactivating your NIC would work for this.

I will be assuming your NIC is eth0 and that it is set up for DHCP, if this is not the case, please post again.

Here is some information on how to set up cron jobs: 
[https://wiki.ubuntu.com/CronHowto](https://wiki.ubuntu.com/CronHowto)

What I would do is something like this (all in terminal):

1. ```
 export EDITOR= nano  
```

To let nano temporarily be able to edit the crontab (makes it easier if you don't know how to use vi, if you do, just forget this).

*EDIT: looks like nano is default for editing contabs for me at least, so this step looks like it may be omitted (but it doesn't hurt to leave it there).

2. ```
 sudo crontab -e 
```

To edit the crontab with nano and schedule the job as root (which will be needed for the job to work in this case).

Now, here is where you'll add you jobs for cron.

The format is: ```
 * * * * * <command> 
``` 
Where each asterisk represents going from left to right:

min (0 - 59)
hour (0 - 23)
day of month (1 - 31)
month (1 - 12)
day of week (sunday=0, 0 - 6) 

For this, you should only need to edit the hour part.

So what would the lines look like? 

a)

To deactivate your connection (assuming your NIC is eth0) it would look like this if you want to turn it off at midnight:

```
0 0 * * * /sbin/ifconfig eth0 down 
```

b)

To reactivate your connection at say 9:00 am (assuming you're using DHCP with an IP provided by either your ISP or router)
Note: If it's a static IP, you can leave our the line with dhclient

```
0 9 * * * /sbin/ifconfig eth0 up
0 9 * * * /sbin/dhclient
```


So, one you enter these three lines in the crontab, save and exit by pressing control + X and saying yes to saving buffer.

It would be good to test it out first (again changing times to something more appropriate).


[B]NOTE: Change the times this is to be run (deactivation and activation) to those that suit you.
[/B]
NOTE: This looks like a lot, by I type too much. This whole procedure should take 1-2 minutes or less to do once you're comfortable with the steps.



Hope this helps

---

### Post by bushtor on 2006-02-21
Nice trick, which I can use temporarily.  ;-)

However I need to be able to distinguish between different users in the future so maybe I need to get back to the iptables approach.  Maybe some others here have suggestions of gui firewall software with more options than firestarter?

Tor

---

