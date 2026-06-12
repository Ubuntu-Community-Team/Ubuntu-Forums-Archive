---
title: "Question about applications requesting my password to write to certain directories"
date: 2014-05-07
forum: Any Other OS
---

### Post by david209 on 2014-05-07
I apologise for the terribly-worded title (and post); I honestly had no idea how to phrase any of this!

I've got a question about how certain applications on *buntu ask for permissions when attempting to do something that requires administrative privileges. I'll be using the *NVIDIA X Server Settings* application as an example, although there are many on *buntu that also do the same thing.

When I attempt to save my configuration file to **/etc/X11/xorg.conf**, I'm given a permission error by the NVIDIA application and then prompted to enter my password, as shown below:

[IMG]https://i.imgur.com/TPNaJ2G.png[/IMG]
My question is: what's making this possible? I recently tried openSUSE, and in the same situation it just threw up the error and I was left to create the file manually (or launch the application as **root**). From the screenshot, I'm guessing it's **PolKit** running on *buntu that's allowing applications to request permissions like this. After clicking that *Screen Resolution Extra* link, I'm taken [here]("https://launchpad.net/screen-resolution-extra"). So, from what I'm guessing, as a *complete* beginner, is that the application is using PolKit (something I don't know anything about), which is somehow identifying what it's trying to do (presumably by using a GNOME application or pretending to be one(?)), which in turn is giving it administrative privileges just to do that action.

If I'm wrong, please help me understand how this works. I'd really appreciate it. As if I wanted to manually give another application, like Kate, this functionality or something. I'm just a newbie trying to understand something new.

---

