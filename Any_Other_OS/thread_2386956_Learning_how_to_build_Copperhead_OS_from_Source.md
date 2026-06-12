---
title: "Learning how to build Copperhead OS from Source"
date: 2018-03-12
forum: Any Other OS
---

### Post by mr.travo on 2018-03-12
I am needing someone with a little bit of patience to help me learn how to build Copperhead OS from source. I have never done one before and want to learn what I am doing. I am pretty computer savvy, this is just something pretty new to me. The directions are pretty straight forward (it seems) but others are telling me you need to understand some code to understand what's going on and have a bunch of software installed first. 

The instructions can be found here- [https://copperhead.co/android/docs/](https://copperhead.co/android/docs/) 

Has anyone tackled this Android OS before? 

Thanks guys!

T

---

### Post by mr.travo on 2018-03-12
I have also (somehow) messed up with the GPG keys and Copperhead won't verify the keys. This is is my output:

```

**ubuntu@ubuntu16:~/copperheados-OPM1.171019.021.2018.03.10.15$**repo init -u https://github.com/CopperheadOS/platform_manifest.git -brefs/tags/OPM1.171019.021.2018.03.10.15


Your identity is:XXXXXXXX <XXXXXXX@XXXXX.com>
If you want tochange this, please re-run 'repo init' with --config-name


repo has beeninitialized in/home/ubuntu/copperheados-OPM1.171019.021.2018.03.10.15

**ubuntu@ubuntu16:~/copperheados-OPM1.171019.021.2018.03.10.15$**gpg --recv-keys 65EEFE022108E2B708CBFCF7F9E712E59AF5F22A
gpg: no keyserverknown (use option --keyserver)
gpg: keyserverreceive failed: bad URI

```

Name and email was censored.

---

### Post by mr.travo on 2018-03-12
How do I switch this GPG key back to the way it is supposed to be when you install the system? I don't use keys, I don't need them, and really could care less about them. 

T

---

### Post by coffeecat on 2018-03-13
*Thread moved to **Any Other OS**.*

---

### Post by kerry_s on 2018-03-13
> **mr.travo said:**
> How do I switch this GPG key back to the way it is supposed to be when you install the system? I don't use keys, I don't need them, and really could care less about them. 

T

it's just a bad command, nothing to worry about.
"gpg --recv-keys 65EEFE022108E2B708CBFCF7F9E712E59AF5F22A" is incomplete, not the proper command.

---

### Post by mr.travo on 2018-03-14
Thank you Kerry. 

I am following some given instructions, somehow my GPG has gotten screwy and I am trying to figure it out. This is a fresh install of Ubuntu 16.04 so I really don't understand why it's given me so much grief...

---

### Post by kerry_s on 2018-03-14
do an update in terminal: sudo apt update

if it gives an error copy & paste the error here

---

