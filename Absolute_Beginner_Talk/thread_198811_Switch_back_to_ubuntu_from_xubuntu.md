---
title: "Switch back to ubuntu from xubuntu"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by babyboss on 2006-06-17
Hello I am too bored, and I tired xubuntu.. but now I can't switch back to my ubuntu. what can I do? Reinstall?

---

### Post by stupidkid on 2006-06-17
Since Xubuntu is basically Ubuntu with Xfce. You can just install Gnome and then remove Xfce if you want to save space.

---

### Post by babyboss on 2006-06-17
what about edubuntu?

---

### Post by user1397 on 2006-06-17
edubuntu is more for school/class oriented computers.  it has a lot of educational programs built-in.

as for your situation, i would follow this guide: [http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php) to remove all of the xubuntu packages.

---

### Post by catlett on 2006-06-17
Did you have Ubuntu and then you went to Xubuntu? How did you switch? Did you just install xubuntu-desktop? Did you do a reformat and install with a cd of xubuntu?

I'll assume you did the most extreme and you reformatted and installed xubuntu from a cd. Just enter this in the terminal ```
sudo aptitude install ubuntu-desktop
``` You will get a prompt telling you you can have only 1 default  session manager. Click O.K. The next page asks you which one you want , choose "gdm". Gdm is gnomes session manager. Choosing this make gnome (and thus ubuntu) your default window manager on start up.

After the install reboot. When you get to the login page go to the "options" in the lower left hand corner. Click on that, choose select session. This is where you can choose Ubuntu or Xubuntu. Ubuntu is gnome and xubuntu is xfce. You can chose either one from now on. This way yoiu get ubuntu back but still have xubuntu if you want it.
By choosing gdm earlier the "default system session" is ubuntu so choose that at the first reboot. After that you can just login and get ubuntu. You only need to go back into options if you want xubuntu.

If you really hate xubuntu. When you reboot and you get into ubuntu, enter this command to get rid of it ```
sudo aptitude remove xubuntu-desktop
```

---

### Post by aysiu on 2006-06-17
[QUOTE=babyboss]Hello I am too bored, and I tired xubuntu.. but now I can't switch back to my ubuntu. what can I do? Reinstall?[/QUOTE] What do you mean you "can't switch back"? Are you saying Gnome doesn't appear in the Session menu?

---

### Post by babyboss on 2006-06-17
Thank you all for your response. I just finished reinstalled everything, and updated to the new version.

---

### Post by user1397 on 2006-06-18
catlett, remember to always recommend ```
sudo aptitude update && sudo aptitude install foo
```because without the update, aptitude doesn't really work.  thanks to aysiu for pointing that out a billion times.

---

### Post by yamagami on 2006-06-18
Had the same issue - installed xubuntu-desktop (via synaptic). Though my problem was lost sound afterwards. 
So, I started the long cmd line suggested by the tutorial to remove xubuntu. 
A bit into it, i noticed it is about to remove thunderbird, and other usefull stuff like apache mods and whatnot. So i stopped the process as it didn't seem right....
anyone knows anything about that? why would removing xubuntu involve removing thunderbird, alien, kismet etc.? these were installed before i installed xubuntu!

Thanks,
Harel

---

### Post by catlett on 2006-06-18
[QUOTE=erik1397]catlett, remember to always recommend ```
sudo aptitude update && sudo aptitude install foo
```because without the update, aptitude doesn't really work.  thanks to aysiu for pointing that out a billion times.[/QUOTE]
What is "foo". I just did a search in synaptic package manager and it is not listed. I haven't seen Aysiu mention it before. If I see Aysiu in a thread I don't bother browsing it. Aysiu being there means everything is being taken care of. But it appears I may have to do a quick check in on Aysiu's posts so I don't miss anything usefull. BTW.. what is foo and why isn't it in synaptic when I have every ubuntu repository you can have in my repository list?

---

### Post by user1397 on 2006-06-18
[quote=catlett]What is "foo". I just did a search in synaptic package manager and it is not listed. I haven't seen Aysiu mention it before. If I see Aysiu in a thread I don't bother browsing it. Aysiu being there means everything is being taken care of. But it appears I may have to do a quick check in on Aysiu's posts so I don't miss anything usefull. BTW.. what is foo and why isn't it in synaptic when I have every ubuntu repository you can have in my repository list?[/quote]When someone in the forums says "sudo apt-get install foo" or "sudo aptitude install foo", foo is just an example. Lots of times in the wiki or other places, it'll say "if you want to install the package foo in the terminal, all you would do is "sudo apt-get install foo"".  It's the same thing as saying "sudo aptitude install <packagename>".  So therefore, its not in the repos, because its not a package! It's just a way to explain things.

oh and btw, aysiu does take care of a thread almost instantly like you say, but i dont think he likes being praised so much (at least thats my experience)

---

### Post by catlett on 2006-06-18
[QUOTE=erik1397]when someone in the forums says "sudo apt-get install foo" or "sudo aptitude install foo", foo is just an example.  it's the same thing as saying "sudo aptitude install <packagename>"  So therefore, its not in the repos, because its not a package!  it's just a way to explain things.

oh and btw, aysiu does take care of a thread almost instantly like you say, but i dont think he likes being praised so much (at least thats my experience)[/QUOTE]

I get it. I'm a bit old for for my age. "widget" was the example term when I was in school. Thanks for the quick reply. One thing about you, you never leave anyone hanging in a thread. :grin: See you around.

---

### Post by user1397 on 2006-06-18
[quote=catlett]Thanks for the quick reply. [/quote]you're welcome[quote=catlett]One thing about you, you never leave anyone hanging in a thread.[/quote]i could also say the same about you [quote=catlett]:grin: See you around.[/quote]you too!

---

