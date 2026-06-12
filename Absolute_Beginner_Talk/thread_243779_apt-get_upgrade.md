---
title: "apt-get upgrade"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Mr.er on 2006-08-25
when typing 

```

sudo apt-get update && sudo apt-get upgrade

```


into the terminal, I get the following errors.

```

Get: 13 http://archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Fetched 104B in 0s (224B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I have no idea how to go about fixing this. 

ANY help is very appreciated.

---

### Post by Metacarpal on 2006-08-25
Do you have any other program installation/upgrade processing running?  Examples would be Synaptic, Add/Remove (in the Apps menu), the Update Manager, or possibly building a package from source (though I'm not too sure about that last).

If so, close those first before doing your upgrade.

---

### Post by aysiu on 2006-08-25
Do you have the update manager or Synaptic Package Manager or Adept open?

---

### Post by b_martinez on 2006-08-25
I think thatit is because you have 'apt-get update' going at the same time that you are trying to run 'apt-get upgrade'. Both use dpkg. Of course I could be totally wrong.
Bill

---

### Post by Metacarpal on 2006-08-25
> **aysiu said:**
> Do you have the update manager or Synaptic Package Manager or Adept open?

jinx! ;)

---

### Post by bulldog on 2006-08-25
Nice going Mr.er.

Twice the same question in two topic's.

You must be desperate. lol

---

### Post by Mr.er on 2006-08-26
sorry i pressed submit twice like an idiot.

i got it sorted tho, i had the synaptic manager running.

---

### Post by Frank Golden on 2006-08-26
> **b_martinez said:**
> I think thatit is because you have 'apt-get update' going at the same time that you are trying to run 'apt-get upgrade'. Both use dpkg. Of course I could be totally wrong.
Bill
Actually Bill that command tells the computer to do the the apt-get update first then when finished do the apt-get upgrade. One after the other not at same time.

---

