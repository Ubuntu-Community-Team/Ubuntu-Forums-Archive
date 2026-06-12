---
title: "E-Mail &amp; Newsreader"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by Boxkar on 2005-12-08
Real new to ubuntu but enjoying the ride thus far.  I have Evolution Mail configured and it seems to be working OK but with one or two things that I don't understand.  Also configured it to run as a newsreader.  The option to 'Hide Read Messages' will not stick...set it now and the next time I come back, it is 'unset'.  Also, no 'check' mark is added to the option.

As a newsreader, the program does not seem to work 'off-line'.  Past habit may have to be modified but I like to collect my news sources and then read them later off-line.    Can Evo be set to do that or is it strictly an 'on-line' reader?

Should I be looking for another 'news reader'.

Thanks for any comments.

---

### Post by Rumor on 2005-12-08
Hi and welcome!

I'm new to ubuntu too. I can't answer your question about the email, but I can recommend a different news reader. If you've ever use Free-Agent or Agent in a windows environment, then you will probably like Pan. Pan is a very full-featured news reader. To install it (going from memory here)

1. System | Administration | Synaptic Package Manager
2. Search for Pan
3. Check it, Mark for installation.
4. Click Apply
5. Let Synaptic do its thing.
Now, for some reason, Pan does not show up in the applications menu (or at least it didn't for me) To get it to show up is easy, though.

Open your terminal (Applications | Accessories | Terminal)
type: 
```

sudo killall gnome-panel restart

``` and press enter. (Enter your password)
Pan should now appear in your Applications | Internet program group.

---

### Post by ogregore on 2005-12-08
Boxcar,

I agree w/Rumor.  IMO it is better to have a specialized tool for a job.

I have used Evolution w/other distros (SuSE, YOPER) but for whatever reason I am not as comfortable with the newest version.  For e-mail I am happy with Mozilla Thunderbird, it has an email tool interface instead of a "groupware" look and feel, it will also do newsgroups but I use Pan for that because it feels more like the program I used to use with Windoze (XNews or something like that, it's been a while).

The great thing about Ubuntu and other Deb distros is that you have apt to get whatever (mostly) you want or need. With Open Source and the GPL you can experiment as much as you feel like it without having to "return unopened packages for a refund".

Cheers
Ogre

---

### Post by Boxkar on 2005-12-12
Thanks for the responses.  Now to see if I can do an apt on Thunderbird!  

Boxkar

---

