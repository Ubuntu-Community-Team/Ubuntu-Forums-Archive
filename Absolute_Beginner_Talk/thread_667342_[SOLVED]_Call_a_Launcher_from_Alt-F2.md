---
title: "[SOLVED] Call a Launcher from Alt-F2?"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by jjsonp on 2008-01-14
Let's say I create a launcher and put it in my home folder.

How can I call that launcher by typing its name into Alt-F2? And, assuming that's possible, what folder would I have to put the launcher in so as to not have to type a folder prefix?

Thanks.

---

### Post by iris-n on 2008-01-14
It's possible.

To launch it, you just type the whole path there and click execute. Have you already tried? Which error did you get?

To execute without typing the path, you have to add the folder your program's in to the PATH variable. How?

```
sudo nano ~/.bashrc
```

there, you add this line

export PATH=$PATH:/home/<your_name>/<your_folder>

Although it's a little inelegant to add all folder. I just created a folder in my home called bin, and moved all my programs there.

---

### Post by Dr Small on 2008-01-14
I'm thinking that jjsonp wanted it to launch the application by pressing ATL + F2.
I can easily do this in IceWM with the .icewm/keys file, but I don't know how to do this in Gnome.

Dr Small

---

### Post by jjsonp on 2008-01-14
Thanks; Iris-N had it right. I want to hit Alt-F2, then type the name of my launcher, then execute.

My plan is to make launchers for all of my commonly-launched programs, then put them in a single folder named with very short names that I find easy to remember (like 'fox' for firefox or 'rterm' for root terminal). That way I can launch those apps quickly and easily via custom text-command.

---

### Post by iris-n on 2008-01-14
=)

Well, this i use mostly for my personal programs and scripts. To launch the system apps quickly, i use System->Preferences->Keyboard Shortcuts.

See the way you like better.

---

### Post by Dr Small on 2008-01-14
> **jjsonp said:**
> Thanks; Iris-N had it right. I want to hit Alt-F2, then type the name of my launcher, then execute.

My plan is to make launchers for all of my commonly-launched programs, then put them in a single folder named with very short names that I find easy to remember (like 'fox' for firefox or 'rterm' for root terminal). That way I can launch those apps quickly and easily via custom text-command.
Sorry. I misunderstood.

Dr Small

---

### Post by jjsonp on 2008-01-14
Iris-N, can't seem to get this to work.

I created a folder named 'launchers' under my user-folder (jason).

Then I edited the file you specified, adding the Path. I logged out and logged back in.

I created a launcher named 'fox', which starts up Firefox when I click it, and placed this in my /launchers folder.

I bring up Alt-F2, type 'fox' and I get an error "Could not open location '///file:fox'.

When I run '/home/jason/launchers/fox' from Alt-F2, that generates a similar error...but that's because launchers apparently have a (hidden) extension of 'desktop' (found out when auto-complete added that on). So if I run '/home/jason/launchers/fox.desktop' from Alt-F2 it finds the file.

But instead of launching it, it opens it up in a text-editor!

---

### Post by jjsonp on 2008-01-14
Iris-N, with regard to keyboard shortcuts - I will definitely do that. The only problem I find with keyboard shortcuts is that I inevitably run out, they can be difficult to remember if you have a lot, and sometimes the ones I want are already mapped for some other app.

On Windows I use this amazing utility called SlickRun, which is just a tiny textbox activated by a keyboard shortcut; you can create as many text-based shortcuts as you want, plus stack multiple shortcuts, add parameters, etc. I find it indispensable on Windows and I'd really like to find a way to reproduce that functionality on Ubuntu.

---

### Post by Dr Small on 2008-01-14
How are you making these launchers? Are they bash scripts?
If so, they will need to have executable permissions to run.

Dr Small

---

### Post by iris-n on 2008-01-14
I'm sorry, jjsonp, i had never tried to do these with launchers. I have made now, and it didn't worked on my machine too.

I tried changing the permissions to, Small, to no effect.

However, i found a workaround. Instead of launchers, i made symbolic links.

That's the way:

Open your terminal, browse to your launchers folder. Type: ```
ln -s /usr/lib/firefox/firefox fox
```

and it's ready!

replace /usr/lib/firefox/firefox with the path to the application you want, and fox with the name you want it to have =)

---

### Post by jjsonp on 2008-01-14
Thanks Iris-N; I will do that. What does the 'ln' do though - is it adding that line to a config file somewhere or something? Also, you say to browse to my 'launchers' folder, but from what you executed it didn't seem like it would matter where I called it from? Anyway, I will play around with it - thanks a lot!

Dr Small, I was referring to the GUI 'launchers' you create in Gnome; I made mine by right-clicking on the desktop then choosing 'create launcher'.

---

### Post by Dr Small on 2008-01-14
To browse to you launcher's directory (where ever you may have it):
```
cd /path/to/launchers
```

Example, if your launchers directory is located in /home/drsmall/launchers, you would do the following:
```
cd /home/drsmall/launchers
```

The ln -s stands for "link symbolic from to.
So, after you have changed directory to your launchers, run:
```
ln -s /usr/lib/firefox/firefox fox
```

Which would make a symbolic link from **/usr/lib/firefox/firefox** to **/home/drsmall/launchers/fox**

Dr Small

---

### Post by SanskritFritz on 2008-01-14
Maybe an alternative could be aliasing commands. That would be easy to call from the calt-F2 dialog.

---

### Post by jjsonp on 2008-01-14
Hey that works great Iris-N! I see that it creates a bash script.

Can I modify the script or change a setting so that I'm not prompted when I try to execute the script? I realize this is a security risk, but if I could perhaps designate only that folder as 'safe' or something (or individually within these scripts) that would be acceptable for me.

---

### Post by Dr Small on 2008-01-14
> **SanskritFritz said:**
> Maybe an alternative could be aliasing commands. That would be easy to call from the calt-F2 dialog.
Yes, that would be just as simple.

---

### Post by jjsonp on 2008-01-14
Dr Small or SanskritFritz: can you provide an example of how to implement the aliasing?

The symbolic link method works, but unfortunately prompts me with a dialog when I call it which I'd like to avoid for launching purposes.

---

### Post by Dr Small on 2008-01-14
First, create an aliase file if you don't have one.
```
touch .bash_aliases
```

Then implement it like this:
```
alias fox="firefox"
```

Save it, and now your alias should work.

Dr Small

---

### Post by p_quarles on 2008-01-14
> **Dr Small said:**
> First, create an aliase file if you don't have one.
```
touch .bash_aliases
```

Then implement it like this:
```
alias fox="firefox"
```

Save it, and now your alias should work.

Dr Small
+1

Btw, you'll have to open a new terminal before the new alias will work.

This is definitely the easiest way to accomplish what you're after here.

---

### Post by jjsonp on 2008-01-14
Thanks Dr Small. However that doesn't seem to work. Do I need to put the bash alias file in a particular directory?

---

### Post by p_quarles on 2008-01-14
> **jjsonp said:**
> Thanks Dr Small. However that doesn't seem to work. Do I need to put the bash alias file in a particular directory?
You'll need to edit .bashrc:
```
sudo nano .bashrc
```
Then, uncomment the following three lines:
```
#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi
```

---

### Post by jjsonp on 2008-01-14
Okay I've uncommented those lines, logged out, logged back in...still no luck.

I can't find that alias file I created anywhere although I know I saved it. I was in my /home/jason/launchers folder at the time but I'm not sure where that file saved to.

---

### Post by jjsonp on 2008-01-14
I enabled system/hidden file viewing...now in /home/jason I see a '.bash_aliases' file and a '.bashrc' file. The aliases file has the entry described in it, and those lines are uncommented in .bashrc. I logged out, logged back in...but hitting Alt-F2 and typing 'fox' produces a 'file not found' error.

Does the .bash_aliases file require some sort of header in it? The only thing I put in the file was:
alias fox="firefox".

---

### Post by jjsonp on 2008-01-14
Okay, here's why it kept failing: the alias works fine from the terminal, but doesn't work from Alt-F2.

---

### Post by SanskritFritz on 2008-01-14
oops, sorry, I didn't know that! What if you turn on the "run in terminal" option? Sorry cannot test here, I'm on windows here at my workplace...

---

### Post by jjsonp on 2008-01-14
Nope, checking the 'run in termal' box generates the same error "Could not open location 'file:///fox'. The location could not be found". Somehow Alt-F2 has to be told to check the aliases I guess.

I am on Windows at work too, but I installed VirtualBox and Ubuntu in a VM;) - works great.

---

### Post by jjsonp on 2008-01-14
Okay, I got the symbolic link to work without prompting by placing it in /usr/bin.

The aliases method seems cleaner in a way - a single line of text in a single file. If anyone knows how I can get Alt-F2 to interpret the aliases I'll go that route.

Thanks. I'll leave this thread open for a while to see if there are any other comments, but I'll mark it as 'solved' soon.

---

### Post by p_quarles on 2008-01-14
My guess is that the run dialog (alt-F2) you're using is not executing those commands in Bash, but rather one of the other shell environments available on the computer. If you can find out which shell it's using (probably dash[=Debian Alquist Shell]) then you can probably set up a configuration file for it that's similar to .bashrc. 

I say "probably" because I've never tried anything like that, and you're guess is as good as mine as to whether that will work.

---

### Post by iris-n on 2008-01-14
It isn't recommended to leave the files there, it's easier to mess in a reinstall.

In my computer i wasn't prompted to anything. Exactly what message do you get?

---

### Post by SanskritFritz on 2008-03-31
I just found this gem: [http://do.davebsd.com/](http://do.davebsd.com/)
Give it a try, if you ever heard of Quicksilver, and love the idea, you will like this!

---

