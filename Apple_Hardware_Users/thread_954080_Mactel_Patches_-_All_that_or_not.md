---
title: "Mactel Patches - All that or not?"
date: 2008-10-20
forum: Apple Hardware Users
---

### Post by jwhendy on 2008-10-20
Hi,


I use Zenwalk but love the Ubuntu community for it's support and especially because it's a great place to get a lot of input as there are a lot of users!

I'm compiling a new kernel and while I'm at it trying to figure out if I need/should use the mactel patches. Currently they are only updated to 2.6.26.* kernels and I'm trying to use kernel 2.6.27... When I compiled my first kernel, I thought I needed them for touchpad support and some other things, but I just compiled 2.6.27.2 without any patches and everything works fine thus far (well, except wireless, but I'm working on it). 

For reference, here's the list of the patches (for 2.6.26.*) I'm talking about:

applesmc-accel-create-check.patch
applesmc-int-protect.patch
applesmc-macbook-air.patch
applesmc-macbook-v3.patch
applesmc-remove-debugging-messages.patch
applesmc-retry-when-accessing-keys.patch
applesmc_int.patch
appletouch-new.patch
appletouch.patch
disk-protect-2.6.26.patch
disk-protect-update.patch
export-lookup_dev.patch
fix_fn_key_on_macbookpro_4_1_and_mb_air.patch
sigmatel_audio_fix_when_module_parameter_is_set.patch

I don't know what all of them do, so if you do, it'd be helpful to post an explanation (for me and the others who might visit this page). I think that the applesmc patches have to do with the System Management Controller (temperature sensors, accelerometer to detect a fall, sleep/wake, backlights, etc.). Appletouch sounds like trackpad perhaps. That's about all I know...

So, do you Apple users use the patches, are they all that helpful, what advantages/disadvantages do you see with them, etc.? Now it's time for you other Linux on Mac users to chime in! If users here think they are definitely worth it, I'm going to fiddle with 2.6.26 to see if I can get them to work for the 2.6.27 kernel.

Thanks so much - I do appreciate your input!

-John

---

### Post by cyberdork33 on 2008-10-20
I do not use them, but I just use the default Ubuntu kernel.

There is a mactel-linux mailing list. They maybe able to answer your questions better on there.

---

### Post by kosumi68 on 2008-10-21
The applesmc patches are obsolete as of upstream kernel 2.6.28, and Intrepid kernel 2.6.27-7.

---

### Post by jwhendy on 2008-10-21
Thanks for the replies so far.

- I take it that by 'obsolete' these features are incorporated in newer kernels? Or does 'obsolete' just mean that they are not being updated for integration into the vanilla kernel sources post 2.6.28 (and the Intrepid kernel you reference)?

- That leaves for potential benefit only:
1. Appletouch patches: my touchpad works fine without this applied in 2.6.26.6 and 2.6.27.2 (except that I wish I could find a non-invasive ctrl+click=right click method).

2. Disk protect patches: for falls/drops?

3. Export-lookup patch: no idea

4. Function key fix: doesn't apply to me

5. Audio fix: my computer makes sound so I'm happy :)


Thoughts? I think we're making progress weeding through what may be helpful for those with Macs and what is unecessary. I'm learning!

-John

---

