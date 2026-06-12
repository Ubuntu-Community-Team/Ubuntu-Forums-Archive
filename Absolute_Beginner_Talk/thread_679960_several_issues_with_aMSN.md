---
title: "several issues with aMSN"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by FDDave on 2008-01-27
I seem to have a lot of problems here. For one, I can't click any URLs. If I do, I get this error message.

"Can't execute application: mozilla $url. Check preferences."

I'm still pretty much a noob to all of this, so that tells me nothing. I can copy and paste the links, but it's an inconvenience when multitasking.

Second, (and this one is not so much an aMSN problem, as an overall Linux issue I seem to be having), I wanted to install a plugin. In order to do that, I need to extract the ZIP file into the plugins folder. The only problem is that only the root profile has permission to do that, and I have no idea how to access my root profile. I was never given the option to set one up, and I'm still unfamiliar with the terminal.

Finally, I can't seem to upgrade, which seems to have something to do with not being able to click links. I told it to remind me in a week, so I'm not sure what's going on there.

Can anyone help me out with all of this?

---

### Post by y-lee on 2008-01-27
> For one, I can't click any URLs. If I do, I get this error message.

"Can't execute application: mozilla $url. Check preferences."

It seems ubuntu is trying to open mozilla and it is not installed, or maybe firefox. Click System ---> Preferences ---> Preferred Applications. Under the Interent tab, web broswer what does it say? I have mine set to custom and the command to 

```
swiftweasel "%s"
```

because i use swiftweasel instead of the official firefox. If you wantto open firefox when ya click on links change to

```
firefox "%s"
```

---

### Post by FDDave on 2008-01-27
It wasn't in the system preferences, but in the aMSN preferences, but that helped me figure that out, so thank you very much. I had to change it to "firefox $url" instead of "mozilla $url"

Now if only I could figure out this whole root mess.

---

### Post by y-lee on 2008-01-27
> Second, (and this one is not so much an aMSN problem, as an overall Linux issue I seem to be having), I wanted to install a plugin. In order to do that, I need to extract the ZIP file into the plugins folder. The only problem is that only the root profile has permission to do that, and I have no idea how to access my root profile. I was never given the option to set one up, and I'm still unfamiliar with the terminal.

There are several ways to deal with this. An easy one is to first download and extract the file to someplace like your desktop and then start nautilus in superuser mode by opening a terminal and typing in : 

```
gksudo nautilus
```

Give your password of course.

Now by sure aMSN is closed and then naviagate in nautilus (the file manager) to your aMSN plugin folder and drag the plugin folder you extracted on your desktop into the aMSN plugin folder in Nautilus. Close Nautilus.

Start aMSN and see if your plugin shows up. If so party time :popcorn:

---

### Post by y-lee on 2008-01-27
> It wasn't in the system preferences, but in the aMSN preferences, but that helped me figure that out, so thank you very much. I had to change it to "firefox $url" instead of "mozilla $url"

Yep I just noticed that myself when i opened aMSN. Links for me opened in firefox instead of swiftweasel which i just recently installed, so i had to fix it.:)

If you open aMSN in superuser mode it can update its plugins for you, i also just noticed that.

```
sudo amsn
```

If plugins need updated it should find them automatically.

---

### Post by y-lee on 2008-01-27
If no one else helps ya with updating Amsn I will after I get back from the store. I'm walking so it may take a while :)

---

### Post by FDDave on 2008-01-27
Thank you so very much. This fixed pretty much everything.

---

### Post by y-lee on 2008-01-27
If you still wish to update aMSN to the latest version I first need to know How you installed it. aMSN in the repos is a bit old. And btw clicking on the aMSN Homepage link in the windows that pops up when ya start aMSN and it tells you about an update takes you to [The aMSN homepage]("http://www.amsn-project.net/"), :lolflag:

aMSN can't automatically update itself, you have to do it manually :(

---

