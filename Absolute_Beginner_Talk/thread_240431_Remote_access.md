---
title: "Remote access"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by MikeMLP on 2006-08-20
I hear that there is a way to tunnel the windows of one linux machine onto the screen of another machine, similar to the windows remote desktop feature.  I also hear that there are some very serious security risks involved.  What I am looking for is a howto that will show me both how to do this, and what extra security steps I need to take.

Thanks!

---

### Post by Kilz on 2006-08-20
[SSH is what you may be looking for.]("https://help.ubuntu.com/community/SSHHowto") But I wouldnt install it on my computer. Just way to much of a risk.

---

### Post by mssever on 2006-08-20
If you want to use SSH for renning remote graphical programs locally, you need to enable SSH tunnelling. I do it this way:
Edit /home/youruser/.bashrc and put the following at the end:
```
# Source the aliases, if a separate file exists
if [ -e $HOME/.alias ]; then
  [ -n "$PS1" ] && . $HOME/.alias
fi

``` Then create a new file named .alias and put it in your home directory. Put the following there.
```
alias ssh='ssh -o ForwardX11=yes'
``` 
Now, type [FONT=Courier New]source .alias[/FONT]. Assuming you've installed SSH in accordance with the instructions above, you'll be able to tunnel X.

EDIT: BTW, I don't think that SSH is much of a risk, but use your best judgment. AFAIK, it's the most secure way to remotely access a computer. If serious security really is your goal, then you should never connect to your computer remotely (or better yet, never connect to a public network :) ) to the Internet.

---

### Post by akniss on 2006-08-20
> **MikeMLP said:**
> I hear that there is a way to tunnel the windows of one linux machine onto the screen of another machine, similar to the windows remote desktop feature.  I also hear that there are some very serious security risks involved.  What I am looking for is a howto that will show me both how to do this, and what extra security steps I need to take.

Thanks!

[http://www.ubuntuforums.org/showthread.php?t=122402](http://www.ubuntuforums.org/showthread.php?t=122402)

The above HOWTO will show you how to set up VNC on your Ubuntu boxes so that you can manage one or both remotely.  I just used it last week, and have been managing my home server from my laptop since.

---

