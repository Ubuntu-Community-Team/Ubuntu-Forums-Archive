---
title: "Can somebody please help me?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Mr Pink on 2007-11-12
I have been using Ubuntu for some months now and find it fantastic. But then I went to install virtual box via the synaptic packet manager so that i could run some windows programs on top of of my Linux system. This has resulted in some other programs  not working. In fact I have lost my connection to the internet and more importantly, i have suddenly lost the network configuration tool, specifically the ability to connect via a wireless card; they've all just vanished!

i would desperately like some help here and I must confess that I am really not that competent using the command line. does this mean that I will have to reinstall everything again. thanks Mr pink

---

### Post by FranMichaels on 2007-11-12
To answer your post seriously,
Try adding from synaptic, ubuntu-desktop and network-manager-gnome.

See if that helps. :)

---

### Post by mikewhatever on 2007-11-12
Mr Pink, to help you with the network manager, please post the output of the following
> nm-applet

Do you see the icon appear in the panel?

> Do not do the above command!
It will remove everything. rm is short for remove. That is one command to use cautiously.

That command would result in nothing but an error.

---

### Post by FranMichaels on 2007-11-12
> **mikewhatever said:**
> That is not a valid command, use man rm if you need to remove something.

That command would result in nothing but an error.

I don't think it would, but I'm not going to test it. 

I've used rm, what this user wrote would remove all files and subdirectories from where it is run.
-f is for force, with R next to it for recursive
* for all files

It seems correct.

Check this person's posts, they just did it to another forum user, and they lost all their data!
It is a cruel joke :(

I checked wikipedia as well
[http://en.wikipedia.org/wiki/Rm_(Unix](http://en.wikipedia.org/wiki/Rm_(Unix))

The example includes this too, cites it as being used as a joke.

---

### Post by mikewhatever on 2007-11-12
> **FranMichaels said:**
> I don't think it would, but I'm not going to test it. 

I've used rm, what this user wrote would remove all files and subdirectories from where it is run.
-f is for force, with R next to it for recursive
* for all files

It seems correct.

Check this person's posts, they just did it to another forum user, and they lost all their data!
It is a cruel joke :(

Yes, you're right. It would empty the home directory. Thanks to whoever removed that post.

---

### Post by Paul820 on 2007-11-12
> **FranMichaels said:**
> I don't think it would, but I'm not going to test it. 

I've used rm, what this user wrote would remove all files and subdirectories from where it is run.
-f is for force, with R next to it for recursive
* for all files

It seems correct.

Check this person's posts, they just did it to another forum user, and they lost all their data!
It is a cruel joke :(

Man that's just fricking evil. :mad:

---

### Post by Maestro23 on 2007-11-12
> **Paul820 said:**
> Man that's just fricking evil. :mad:

Very evil to do to a noob, I agree.  However, I would look those commands up before I even attempted to use them.:popcorn:

---

### Post by Paul820 on 2007-11-12
People come to these forums for help and they trust the advice that is given to them. Idiots like that just ruin it, thankfully they are few and far between. That person could have had any amount of personal data and treasured photos movies etc. It just really annoys me.

---

### Post by Paul820 on 2007-11-12
Ahh, sorry Mr Pink, have you removed the package again?

---

### Post by mekas2024 on 2007-11-13
Hey guys, i have a question.... i remove the mm-applet from the top panel... but.. i removed by mistake   and now i dont know how to put it on the panel back!!! :S

I remove and reinstall gnome-netrwork-manager but nothing happends... also i installed the knetwork-manager but neither appear when i go to "add to panel" menu clicking the right button over the panel!

Did someone know how to place the nm-applet again in to the applet???
I appreciate if someone gime me a clue of how to do it!

Thanks a lot

Regards

Mekas

---

### Post by spec-chum on 2007-11-13
Right-click on the panel and select Add To Panel.  If you look under System & Hardware there you should see Network Monitor.  Add that.  I think that's the one you want isn't it?

---

### Post by mekas2024 on 2007-11-13
Thanks for the reply, but no, that is not what im looking, thats the network monitor applet that comes with gnome, that i want its the nm-applet, that comes installed with ubuntu, its an applet that show u all the networks avalilable and stuff like that... do u know what im talking about?

Thanks 

Mekas

---

