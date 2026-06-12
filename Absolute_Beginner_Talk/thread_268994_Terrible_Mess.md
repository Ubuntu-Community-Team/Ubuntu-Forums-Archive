---
title: "Terrible Mess"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by i-m-p on 2006-10-01
Nothing works now. All I get is error message when I try to run any applications. Firefox.Gimp..etc.

> The application "gnome-terminal" has quit unexpectedly
restart application
close
inform developers

What I was doing and did was install Japanese package.
First I add repositries two lines.
> deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) dapper/
deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) dapper-ja/
then 
> sudo apt-get update & sudo apt-get install ubuntu-ja-keyring ubuntu-desktop-ja

I just followed this thread
[http://www.ubuntuforums.org/showthread.php?t=188325&page=2&highlight=japanese+font](http://www.ubuntuforums.org/showthread.php?t=188325&page=2&highlight=japanese+font)

It said that "then just reboot and enjoy" I did reboot and it was 
 hell.

Please help. Virtually no application runs now. Even terminal.

Thank you.

---

### Post by sbergman27 on 2006-10-01
Have you tried uninstalling the packages from a text console?

You can hit CTRL-ALT-F1 to get to a text console.

Log in.

and then:

```

sudo apt-get remove ubuntu-ja-keyring ubuntu-desktop-ja

```

Then reboot, and hopefully...enjoy.

---

### Post by i-m-p on 2006-10-01
Thanks, I did remove those two things and then reboot....

Still hell.

No applications open. Just error messages. Luckily enough I still have my old friend in my harddrive.

Please get me out of this hell. Help.

Thanks for your support.

---

### Post by sbergman27 on 2006-10-01
So gnome comes up well enough for you to get to the desktop, but when you click to start an app, it doesn't run, right?

---

### Post by i-m-p on 2006-10-01
Right.

---

### Post by sbergman27 on 2006-10-01
On the graphical login screen, do:

Options->Select Session->Failsafe terminal

Click "Change Session"

and then log in.

You will get a screen with just a terminal window.

in that terminal type:

```
gnome-terminal
```

and see if gnome-terminal comes up.  Note anything that displays in the original terminal.

---

### Post by i-m-p on 2006-10-01
Hello there!

I did and gnome-terminal comes up. And original terminal says nothing.

I am running the browser from ubuntu now. From gnome terminal.

Thanks

---

### Post by sbergman27 on 2006-10-01
OK.  In the original terminal, do you have a '$' prompt on the line after "gnome-terminal"?  If so, type:

 metacity &

That should put borders on the windows and allow you to move them around. (Metacity is the window manager).

See if that much works.

---

### Post by i-m-p on 2006-10-01
No, no $ prompt marks on the original terminal.

---

### Post by sbergman27 on 2006-10-01
OK.  Exit out of the browser.  Then exit out of gnome-terminal.

You should then get a new '$' prompt in the original.

At the prompt, type:

```
metacity &
gnome-terminal &
firefox &
```

And see if you get gnome-terminal and firefox with normal borders, etc.

---

### Post by i-m-p on 2006-10-01
Yes, Now Firefox looks pretty normal. I can change sizes and so on. I did minimize firefox and it disappeared once.

Cheers,

---

### Post by sbergman27 on 2006-10-01
OK.  That's fine.  You don't have a Window list or panel for it to go to when minimized.

So, there is something about your regular gnome session that is causing problems.

I think we should bring that up, and then start gnome-terminal from a text console.  So, exit out of everything.  Close the original terminal and you should get logged out.

```

Options->Select Session->Gnome

```

Click "change session"

and log in.

Let me know when you have finished that.

---

### Post by i-m-p on 2006-10-01
Hi there,

I did.

Options->Select Session->Gnome

Same. Nothing runs.

I am running firefox from Options->Select Session->Failsafe terminal.

Cheers,

---

### Post by sbergman27 on 2006-10-01
OK.  Do the same thing again.  And then we'll switch to a text screen and try to start gnome-terminal.

Once you are in gnome again:

Hit ctrl-alt-f1 to go to a virtual console 1.

Log in.

Type:

```

export DISPLAY=:0
gnome-terminal

```

Note any messages.

Hit ctrl-alt-f7 to get back to gnome, which runs on virtual console 7.

See if it started.

Let me know what messages you got, or if gnome-terminal came up.

---

### Post by sbergman27 on 2006-10-01
I think this might fix you up.

We need to remove the packages that the two you installed dragged in from the repository.

from the failsafe terminal, type this:


sudo apt-get remove language-support-ja language-pack-ja language-pack-gnome-ja ubuntu-ja-keyring ipafont ipamonafont ubuntu-ja-setup-helper kasumi scim-tomoe xfonts-mplus xfonts-shinonome xfonts-ayu

---

### Post by i-m-p on 2006-10-01
Cheers,

First, No messages after 
> export DISPLAY=:0
gnome-terminal

then ctrl-alt-F7

and Gnome-Terminal was running ,as well as, one Error Message.

> Error
The application "nautilus" has quit unexpectedly. You can inform the developers of what happened to help them fix it. Or you can restart the application.
restart application close inform developers.

---

### Post by sbergman27 on 2006-10-01
Just in case you might have missed it, note my post #15 above.  I think it will probably work.

---

### Post by i-m-p on 2006-10-01
Right. I'd missed your post #15.
I did it however the problem remains the same.

I logged in Gnome session. Nothing runs.

I've got no clues what I can do.

---

### Post by sbergman27 on 2006-10-01
In the failsafe terminal:

sudo -s

This makes you root so you don't have to sudo everything.

And then, for each package that I listed, individually:

```

dpkg -P --force-depends packagename

```

where packagename is the package name.

For each one, it should say that it is ignoring the request to remove the package because it isn't installed.

Make sure it says that for each one.

I really think that one of those packages is still installed and causing problems.  A bad font package could easily be the cause of all this.

---

### Post by i-m-p on 2006-10-01
Hi there.

Thank you very very much for your help. You are very kind and knowledgeable. I've got to run now. Thanks to you. I can access internet and most of the application from this session. Hopefully I can fix this very soon.

Sincerely.

---

### Post by sbergman27 on 2006-10-01
Good luck!

BTW, after running the previous commands, you may need to reboot.

-Steve

---

### Post by i-m-p on 2006-10-01
Thank Goodness! Finally I rebooted. Voila! Enjoy!

Thank you very much and I trully applaud your knowledge and kindness.

However one thing. I did everything you said "dpkg -P --force-depends packagename" individually and I rebooted and I rebooted but still there is no 
 "reboot and evjoy" moment. Nevertheless ,almost accidently, I logged in as  options/select session/Failed Gnome. Then there was an updated notice for 20 packages. Next normal login there was a blissfull "reboot and enjoy" moment.

---

