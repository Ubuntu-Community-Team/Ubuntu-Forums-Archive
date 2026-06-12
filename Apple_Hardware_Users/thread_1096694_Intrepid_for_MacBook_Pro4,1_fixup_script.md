---
title: "Intrepid for MacBook Pro4,1 fixup script"
date: 2009-03-15
forum: Apple Hardware Users
---

### Post by philcolbourn on 2009-03-15
I have put together a script to do most of the things listed in [https://help.ubuntu.com/community/MacBookPro4-1/Intrepid]("https://help.ubuntu.com/community/MacBookPro4-1/Intrepid") and related posts.

It will not run unless the hardware is a MacBook Pro 4,1, and it is only for Ubuntu 8.10 (Intrepid).

It could be modified for other Macs and Ubuntu versions if someone has the time.

It is not perfect: the touchpad fdi file works fie but not all the options are set for some reason that I do not yet understand. Everything else seems fine so far.

Lots of things work well: Apple remote, sleep/resume, touchpad (could be better though), display brightness, keyboard backlight and compiz (with Nvidia driver).

The script is written in such a way that any error will halt the script with a (hopefully) useful error message.

At the moment it comes in two parts: a little script to append lines to a file, and the actual install script.

It is safe to run over and over again, even if you have implemented some of the recommendations already - but at your own risk. It should do no harm, but check the files that are modified for any oddness or duplication.

The first script called pc-add-config-line.sh and the main script is called pc-macbook-pro4-1-intrepid-fixup.sh

Both can be installed in your home directory.

---

### Post by primatephreak on 2009-10-03
This is just the type of script I was looking for.

A thousand thanks.

---

### Post by philcolbourn on 2009-10-03
I'm pleased that you have found it useful. If I can be of further assistance, just ask.

Thanks for your reply.

---

### Post by primatephreak on 2009-10-03
Well.. I'm running Ubuntu 9.10 / Jaunty on a Macbook 4,1 ; I suppose your script wont work due to it being written for 8.10 / Intrepid?

I haven't taken a reeeal good look at the code yet, but it should be easy to port it over to 9.10, right?

---

### Post by philcolbourn on 2009-10-03
> **primatephreak said:**
> Well.. I'm running Ubuntu 9.10 / Jaunty on a Macbook 4,1 ; I suppose your script wont work due to it being written for 8.10 / Intrepid?

I haven't taken a reeeal good look at the code yet, but it should be easy to port it over to 9.10, right?

I think you mean 9.04. I don't have a MacBook 4,1 (I do have access to a MacBook1,1 but I have not loaded Ubuntu yet).\

Change the obvious version checks, and check the Ubuntu community instructions for setting-up a MacBook 4,1 for any differences. 

Then let it run. If something fails, it can be commented-out in most instances.

I will be upgrading to 9.10 in a month or so so I will probably be making some changes then.

---

