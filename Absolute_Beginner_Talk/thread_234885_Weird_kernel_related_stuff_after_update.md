---
title: "Weird kernel related stuff after update"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by sanderman on 2006-08-12
Hi, i'm a noob at Linux, having installed Ubuntu yesterday in a dualboot system. After some struggling with the ethernet driver I was finally able to update Ubuntu.

So I pressed the icon in the upper right to update and installed all the updates. After the required restart I suddenly had 2 kernels to choose from in addition to winxp. Is this normal??? The first entry in grubs was the newer kernel with version ending with .26 and does not work (it hangs when trying to start the filesystem), the second and original entry I think was the old kernel with version ending with .23 which still works correctly.

Is this normal? Has anything gone wrong during updating? What should I do now? I would rather have only 1 kernel to choose from at bootup.

---

### Post by steve.horsley on 2006-08-12
It is normal to get 2, 3, etc... kernels listed in GRUB as you install updates. If you want to remove the old ones, you can use Synaptic Package Manager and search for Linux and remove the old ones there, once you are happy that the updated one works. I have not heard of an update failing the way yours has before, but this is why the update doesn't automatically remove the old kernels. I'm not really sure what to do about that. You could search for Linux in synaptic, find the one that doesn't work and mark it for reinstallation, but I don't know if that'll fix it. Marking it for deletion will probably make a mess with other things that now appear to depend on it. 

If it were me, I'd probably completely remove that new kernel, and make a note of the other things it also wants to remove. After removing them, make sure the .debs are deleted from /var/cache/apt/archives/ and then reinstall those things. But That's a bit tricky, and an error in the middle could leave you needing a re-install.

Does anyone else have good ideas?

---

### Post by sanderman on 2006-08-12
While waiting for some more replies from other people that my have more ideas on whats going on and how to fix it. I think in the meantime I'l mark this new kernel for reinstallation to see if that does anything good. How would I go about reinstalling that thing?

---

### Post by drtvasudevan on 2006-08-12
> **sanderman said:**
> While waiting for some more replies from other people that my have more ideas on whats going on and how to fix it. I think in the meantime I'l mark this new kernel for reinstallation to see if that does anything good. How would I go about reinstalling that thing?

yes.
normal to have othere kernals shown.
not normal to have it not working.
remove with the same s/w you installed with.
reinstall

---

### Post by sanderman on 2006-08-12
Hi, im back,

Marking for re-installation and hitting apply did not work so now I think I'm going to remove it and install it again. I just hope nothing will get screwed up. **crosses fingers**

---

### Post by sanderman on 2006-08-12
I have tried to delete the .26 kernel and to install it again, nothing changed about the situation. It won't mount the filesystem.

Unless anyone's got a better idea, I'l just stick to .23 for now and remove the newer one.

Anyone have any suggestions?

And...One more question, can I expect this same problem to happen with other newer kernels whenever I want to update, if I don't fix this now?

---

### Post by drtvasudevan on 2006-08-12
> **sanderman said:**
> I have tried to delete the .26 kernel and to install it again, nothing changed about the situation. It won't mount the filesystem.

Unless anyone's got a better idea, I'l just stick to .23 for now and remove the newer one.

Anyone have any suggestions?
someone said if the system works dont upgrade.
i often have the occsion to recall it.
:oops: 

 > And...One more question, can I expect this same problem to happen with other newer kernels whenever I want to update, if I don't fix this now?
who can say?

---

### Post by sanderman on 2006-08-12
Okay, I'll just leave it as is, for now.

Thanx for the help guys.

---

