---
title: "Skype doesn't work."
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by DrMilo on 2006-08-26
Obviously this isn't specifically about Ubuntu. I had Skype working fine on Windows and it doesn't work on Ubuntu. Furthermore Skype doesn't act the same way! There's an option in Windows to either have Skype control the sound or not. To get Skype working in Windows I had to switch off its sound control. I have read elsewhere that Skype doesn't support Alsa. Currently the sound in Skype is set to /dev/dsp. There doesn't seem to be any way to change it in Skype. I suppose the answer might be to edit some file controlling Skype's sound but I think I've looked through them all and none of them seem to reference a sound device.. I don't think I can inhibit Alsa because that's what got everything else working! Any suggestions?

---

### Post by Kimm on 2006-08-26
The latest stable version of Skype uses OSS audio, an old soundsystem that doesnt support mixing.
There is a beta on the Skype website that uses Alsa. I suggest you use that, its much better! ^^

---

### Post by DrMilo on 2006-08-26
> **Kimm said:**
> The latest stable version of Skype uses OSS audio, an old soundsystem that doesnt support mixing.
There is a beta on the Skype website that uses Alsa. I suggest you use that, its much better! ^^

Thanks! I'm looking at the site now and none of the packages seem to be for Ubunttu. Could you suggest which one?

---

### Post by DrMilo on 2006-08-26
> **DrMilo said:**
> Thanks! I'm looking at the site now and none of the packages seem to be for Ubunttu. Could you suggest which one?

Whoops! Didn't read the fine print. Got it, use the Debian one. Thanks again.

---

