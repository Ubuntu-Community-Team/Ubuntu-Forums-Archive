---
title: "Fan stuck on max speed"
date: 2012-06-23
forum: Apple Hardware Users
---

### Post by 2cute4u on 2012-06-23
I replaced the HD on my  imac and no longer have a  sensor to the HDD, Causing the fan to run at maximum speed all the time.
I had the same problem using OS X but was able to fix in by installing [hddfancontrol]("http://www.hddfancontrol.com/"), which uses the S.M.A.R.T reporting to control the fan.

How can I get  Ubuntu to use the S.M.A.R.T?

---

### Post by kohoutek1 on 2012-06-25
Does anyone know if macfanctrld uses SMART? If so, then 2cute4u might try that.

---

### Post by DoubleClicker on 2012-06-25
> **kohoutek1 said:**
> Does anyone know if macfanctrld uses SMART? If so, then 2cute4u might try that.

macfanctrld doesn't use SMART

---

### Post by 2cute4u on 2012-07-08
I can'tbe the only one who has this problem. What does everyne else do to fix the fan speed?

---

### Post by DoubleClicker on 2012-08-09
I've reported a bug for macfanctd on launchpad, but some reason they are asking for log files,. 

I think they are confusing SMART sensors with SMC sensors.  I will add a new comment, maybe it will get results.

but if you can, please give them your logs

---

### Post by reltson on 2012-10-28
You may have already considered this, but I didn't see it posted...

-unplug your imac
-hold power button for about 5-6 seconds.
-plug in
-power it up

This resets all the SMC controllers in the iMac and should resest the fans.

 If you enter $ sensors  in terminal, and it shows a long list with negative values for temps from most of the sensors, your SMC is stuck.  This will cause the fans to go into overdrive since they aren't being fed any good data from the temp sensors.  Resetting it using the method above will make the sensors put out correct temp data and thereby allow the fans to run at proper speed.

***NOTE: this should work no matter what you have running, i.e. macfanctld, fancontrol, etc.***

---

### Post by mmallmann on 2013-03-13
I am stuck with the same problem. 

I have an iMac(2010) with my own ssd (Vertex3) installed. The hdd fan is on max speed, which is normal since the temperature sensor on the hhd is disabled now. I fixed the problem under OSX through the hddfancontrol.app. 
But I have been looking for ages to find a proper solution for Linux/Ubuntu... but I have not come acrossed one yet...

I would need a program that regulates the hdd fan speed though the S.M.A.R.T. temparature reading of my ssd. 

please help!

---

