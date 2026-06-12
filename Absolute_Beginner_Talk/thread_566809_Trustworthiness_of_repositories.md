---
title: "Trustworthiness of repositories"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by mcbenz55 on 2007-10-03
I realize this is a very open question, but can the repositories that Add/Remove and Synaptic bring up generally be trusted? Are these filtered somehow or is it just every repository Ubuntu can find? I'm worried about installing something with a backdoor or spyware or something else added inside a legitimate program. Furthermore, if I add keys so that software could be authenticated I'm still relying on that repository being trustworthy right?

---

### Post by bsharp on 2007-10-03
There is a text file called /etc/apt/sources.list that is generated when Ubuntu is installed.  You can add and remove repositories as needed, and by default Ubuntu only has the repositories enabled that are maintained by the Ubuntu developers.  There are also third-party repositories that you can add to access additional software based on your needs, and generally I would consider them safe to use.

---

### Post by Dr Small on 2007-10-03
As bshard stated, the default repositories enabled allow you to install software from the Ubuntu Maintained Repository. The Universe and Multi-Universe repositories, which you can enable, and not maintained by the Ubuntu Developer Team, which maintains the default Ubuntu Repositories.

These repositores allow more software to be installed, but may not be considered bug free, completely. You need not worry about viruses and spyware, as Linux is about 98% free of spyware, adware and viruses. Most harmful stuff is written for the majority OS (Microsoft), and even if there was a Viruse written for Linux, it would need proper permissions to be executed to harm your computer, which is why the permissions setup is very nice.

Hope that helps.

Dr Small

---

### Post by defrex on 2007-10-03
Also, if something malicious was to sneak into an Ubuntu repository, you can be certain the internet would be ablaze with the story in no time, as it'd be a first.

---

### Post by Incense on 2007-10-03
If you stick to the default repositories you'll have no worries. As stated the community corrects itself very well. It is the beauty of open source.

---

### Post by bodhi.zazen on 2007-10-03
Well, what is nice about open source, you do not have to take our word for it, you can always download the source code and look for yourself.

At the end of the day you have to put your trust somewhere, but I would trust open source before I trusted anyone who will not let you examine the code ...

Is there a potential for "something to go wrong" , of course, but again with open source where whould you hide the code ?

---

