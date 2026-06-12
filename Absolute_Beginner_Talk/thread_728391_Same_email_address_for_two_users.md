---
title: "Same email address for two users?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Angus77 on 2008-03-18
How can you set up an email account so that two separate users can access it?

Right now I'm using Thunderbird, but I don't really strongly prefer it over anything else.

---

### Post by Hospadar on 2008-03-18
I imagine you are talking about having two different ubuntu users (on the same machine) be able to (through thunderbird) read and send with the same account hosted by someone else.

All you need to do is login as each user and set up the email account in thunderbird for each of them.  If you don't want to do that, you could probably copy (or sybolic link, using ln -s) the thunderbird settings folder in /home/yourusername/.mozilla (I think that's where it is) to the same place in the other users folder.

probably after you figure out where it is, how to set all the permissions correctly, etc, it would probably be a lot easier to just do the multiple setups the traditional way.

You could do the same thing with evolution if you wanted

---

### Post by Angus77 on 2008-03-19
I got it figured out now, althoug I don't know why I have to do it this way.

I ended up making a symlink to the ~/.mozilla-thunderbird/*.default folder in my wife's folder, and then renamed the link to what was listed under Path= in the home/user2/.mozilla-thunderbird/profiles.ini file.

Just to make it easier for myself to understand, I changed the name of the Path in user2's profiles.ini file to the same as mine and then renamed the symlink to the same thing, but then Thunderbird wouldn't start.  I can't imagine why.

Everything seems to be working alright now, though.

---

### Post by hyper_ch on 2008-03-19
why not using two different email addresses?

---

### Post by Angus77 on 2008-03-19
Because we've already given out the address to more people than we're confident we can remember.  At least, that's my wife's excuse!

---

### Post by hyper_ch on 2008-03-19
oh well, I'd setup on the current email address a forwarder two new ones and then use the new ones... so all email that goes to the current one will then be forwarded into each of your accounts... I just like to have thing seperate ;)

However good that you worked out your issue ;)

---

### Post by farueulogy on 2008-03-19
Email isn't like a phone call - it's like a letter. If you want a nice email account each get gmail and it can collect your email from your old address as well into both new accounts.

---

### Post by Angus77 on 2008-03-19
Yeah, I know what your saying, but I've got a Yahoo! account and she's got a Goo account, and then we have this one family account from our provider.  I don't really have a terribly good reason for wanting to do this!

---

