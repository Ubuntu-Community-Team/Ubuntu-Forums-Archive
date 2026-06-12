---
title: "[SOLVED] Ndiswrapper 1.47 does not install correctly"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-09-08
Hi,
I just did a fresh Feisty install and a fellow named 'Anewguy' had helped me learn a week ago how to get my Linksys WMP300N card going. And this was dependent upon my luck of having a backup of Ndiswrapper-1.47 that I can install without having to be online.

And really, I have installed this backup of Ndiswrapper-1.47 almost 6 to 7 times successfully, just by doing this:

Code:

[code]cd Desktop/ndiswrapper-1.47
sudo make
sudo make install[code]

But now with this latest install, it's not installing right. Since that computer is not online, I couldn't paste or print any of the error codes, but here are some snippets of what I'm getting which hopefully will help.

Also btw, I did a second fresh install of Ubuntu from a different live CD thinking that that might solve it but no luck. Here are some of the error codes I'm getting:

Code:

[code]loadnisdriver:c284: Error:  Dereferencing pointer to incomplete type[code]
                        # there are also similar errors numbered c287-289, and 300 on

And here's another one:

Code:

[code]loadnisdriver; c527. warning: Implicit declaration of function 'atoi'[code]


I appreciate any help on this. My whole install of Ubuntu depends upon this, because if I can't get online, why go there.

Many Thanks, Frank B.

---

### Post by Brightbelt on 2007-09-09
I solved this by moving my tower near enough to go wired so I could use Synaptic to install Ndiswrapper. Apparently the utilities and/or dependencies were no longer installing from my backup file.

I wonder why that is? Thanks, Frank B.

---

