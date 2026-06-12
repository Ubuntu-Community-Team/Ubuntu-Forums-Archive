---
title: "I buggered Evolution, is it safe to remove it?"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by bigkahuna on 2006-05-28
Hi,
I tried to setup newsgroups in Evolution following a post I found here, and it not only doesn't work, but Evolution hangs now if I launch it.  I've installed Thunderbird instead (I've used it for years now) and am happy with it.

But that still leaves an app on my HD that, if launched, will hang my system, so I'd like to get rid of it.  My question is this:  can I -safely- remove Evolution using Synaptic?  (I'm afraid that since Evolution was part of the initial distro, removing it might somehow bugger something else up...).

---

### Post by macdo on 2006-05-28
In a terminal, type ```
sudo apt-get remove -s evolution
``` that will simulate the changes to your system. Have a look at the stuff that would be removed, and make an informed decision...

---

### Post by ifokkema on 2006-05-28
[QUOTE=macdo]In a terminal, type ```
sudo apt-get remove -s evolution
``` that will simulate the changes to your system. Have a look at the stuff that would be removed, and make an informed decision...[/QUOTE]

There are quite a few packages having dependencies on Evolution, such as ubuntu-desktop. But don't worry, as this package is just a dummy package that can be removed safely.

Ivo

---

### Post by bigkahuna on 2006-05-28
An informed decision, eh?  Boy, that sounds like a loaded comment!  I'm a noob, so it's likely any decision I make is based on pure dumb luck ;) (more dumb and less luck recently I'm afraid).

I just spent the last day and a half re-installing and trying to configure my system, I'm about 80% of the way to being finished.  I'd really hate to bugger up my entire install and have to start all over again.

---

### Post by ifokkema on 2006-05-28
[QUOTE=bigkahuna]An informed decision, eh?  Boy, that sounds like a loaded comment!  I'm a noob, so it's likely any decision I make is based on pure dumb luck ;) (more dumb and less luck recently I'm afraid).

I just spent the last day and a half re-installing and trying to configure my system, I'm about 80% of the way to being finished.  I'd really hate to bugger up my entire install and have to start all over again.[/QUOTE]

You know what? Provide us the output of the command macdo has given you, and we'll take a look, how does that sound? :)

---

### Post by bigkahuna on 2006-05-28
I opened a terminal, typed in "macdo" and got "bash: command not found".

---

### Post by PhilJ on 2006-05-28
HI,
start synaptic and go advanced mode.
remove all evolution packages except
evolution -webcal
evolution-data-server
then remove .evolution folder from your home folder
 I did and I'm still here using Sylpheed email 

Philj

---

### Post by bigkahuna on 2006-05-28
Thanks Philj.  I did as you suggested, so far I haven't smelled any smoke ;)  BTW, when I opted to remove Evolution, those files you listed were -not- tagged for removal, so I didn't have to change anything.

Thanks again!

---

### Post by ifokkema on 2006-05-29
[QUOTE=bigkahuna]I opened a terminal, typed in "macdo" and got "bash: command not found".[/QUOTE]

I meant: run the command that the user macdo (post 2) gave you:
sudo apt-get remove -s evolution

But if you've done it through synaptic it's all the same.

---

