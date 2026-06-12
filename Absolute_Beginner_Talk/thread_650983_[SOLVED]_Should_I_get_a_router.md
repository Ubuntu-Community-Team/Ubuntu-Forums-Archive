---
title: "[SOLVED] Should I get a router?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by DrMilo on 2007-12-27
I hear from many people that I am insecure without a router even though I am running Linux. I'm not wireless. I'll buy a router if I need to but I was wondering what people on the forums here had to say. Should I buy one purely for security reasons or not?

I also spotted these security recommendations on the web:

Modifying Default Settings

The first set of basic critical changes requires you to modify three insecure default system settings:

    * Reconfiguring shared memory
      Load your favorite text editor, open the file "/etc/fstab" and add the following line of code:

      tmpfs /dev/shm tmpfs defaults,ro 0 0
    * Disabling SSH root login
      Load your favorite text editor, open the file "/etc/ssh/sshd_config" and add change the following line of code:

      PermitRootLogin yes

      to

      PermitRootLogin no
    * Limiting access to the "su" program
      Open the terminal by clicking "Applications" selecting "Accessories" and choosing "Terminal." From there enter the commands:

      sudo chown root:admin /bin/su sudo
      chmod 04750 /bin/su

The final critical change we recommend, is that you protect your personal documents by securing your home directory. The easiest way to do this is by clicking "Applications" selecting "Accessories" and choosing "Terminal." From there enter the command:

chmod 0700 /home/username (replace username with the name you use to login to your computer).

Now that you've successfully made these basic system setting modifications, you're ready to move on and start installing software that protects your system from being compromised.

[http://tinyurl.com/2a5msp](http://tinyurl.com/2a5msp)

I'd be interested in hearing any opinions on these recommendations as well. 

[http://tinyurl.com/2a5msp](http://tinyurl.com/2a5msp)

---

### Post by bodhi.zazen on 2007-12-27
Short answer : IMO, yes

Long answer : What are you looking to gain with a router ?

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by mikewhatever on 2007-12-27
A router would provide another security layer, thus making your computer more secure. Yet, I would not buy one just for that, because Ubuntu is quite secure by itself.

---

### Post by DrMilo on 2007-12-27
Thanks all.

I'm interested in hearing opinions on the shared memory etc. modifications as well.

---

### Post by p_quarles on 2007-12-27
I agree with bodhi, and will just add this point:

If you have an old, slow computer sitting in your closet, you can pretty easily turn that into a NAT firewall, which will essentially do the same thing as a good router. Most likely, you'll need to buy a second NIC for it, but that's going to be about 1 quarter the cost of a decent router. 

As for the other precautions you mention: yes, those are all good things to do.

---

### Post by DrMilo on 2007-12-27
> **p_quarles said:**
> I agree with bodhi, and will just add this point:

If you have an old, slow computer sitting in your closet, you can pretty easily turn that into a NAT firewall, which will essentially do the same thing as a good router. Most likely, you'll need to buy a second NIC for it, but that's going to be about 1 quarter the cost of a decent router. 

As for the other precautions you mention: yes, those are all good things to do.

Thanks I will.

I don't see a forum on here for security and maybe I should suggest one. It seems that Ubuntu is becoming increasingly targeted as it becomes successful and we could all use some more focus on these issues.

---

### Post by bodhi.zazen on 2007-12-27
> **DrMilo said:**
> Thanks I will.

I don't see a forum on here for security and maybe I should suggest one. It seems that Ubuntu is becoming increasingly targeted as it becomes successful and we could all use some more focus on these issues.

I agree. See the link I gave you.

This is the security forum :

[http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7)

---

### Post by DrMilo on 2007-12-27
> **bodhi.zazen said:**
> I agree. See the link I gave you.

This is the security forum :

[http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7)

Ah! I missed that. Still perhaps just making one for security with no qualifiers would be a little more user friendly. So I'll mark this as solved.

---

