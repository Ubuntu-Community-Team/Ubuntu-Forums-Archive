---
title: "Make command not found"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by MoxJet on 2006-06-12
I got around and eventually stumbled upon a few programs that weren't downloadable in binary form, so I read some basics about compiling in linux, but after running the configure I recieved a most peculiar error:

```

dan@Mainframe:~$ make
bash: make: command not found

```
(an output while not compiling anything just to state an example)

Hmm, any ideas why the command can't be found? Is 'make' the command to use or have I been fooled? ^^

---

### Post by IYY on 2006-06-12
sudo apt-get install build-essential

---

### Post by aysiu on 2006-06-12
Can the people who think *build-essential* is a security risk please jump into this thread?

I'm with IYY, though--just go ahead and install it.

---

### Post by taurus on 2006-06-12
[QUOTE=aysiu]Can the people who think *build-essential* is a security risk please jump into this thread?[/QUOTE]
I always think that the normal install should come with gcc and all the goodies to build and install programs from source, just like other Linux distros.  And if you are so concern about security, then leave that stuff out for the server version!  And if there is no space to pack all that stuff into a CD, then have it install automatically upon first boot since it checks for security update anyway!!!  

But hey, it's me so...  :-({|=

---

### Post by catlett on 2006-06-12
That's a good idea. Loading packages that are needed but don't make the single cd install. Why isn't there a first boot "extra install". Kind of like an "extras" cd but over the update manager.
Build essential and a few others always come up. It is a little crazy to think you can't compile on a linux install out of the box.

---

### Post by aysiu on 2006-06-12
[QUOTE=taurus]I always think that the normal install should come with gcc and all the goodies to build and install programs from source, just like other Linux distros.  And if you are so concern about security, then leave that stuff out for the server version!  And if there is no space to pack all that stuff into a CD, then have it install automatically upon first boot since it checks for security update anyway!!!  

But hey, it's me so...  :-({|=[/QUOTE] I agree with you, taurus.

That's why I'm asking all those people who say *build-essential* is a security threat should be jumping in here, but they're not.

---

### Post by aysiu on 2006-06-12
[QUOTE=catlett]That's a good idea. Loading packages that are needed but don't make the single cd install. Why isn't there a first boot "extra install". Kind of like an "extras" cd but over the update manager.
Build essential and a few others always come up. It is a little crazy to think you can't compile on a linux install out of the box.[/QUOTE] Actually, something that came out of the *build-essential* controversy is that *build-essential* is on the CD, even though it's not installed.

---

### Post by nanotube on 2006-06-12
[QUOTE=aysiu]I agree with you, taurus.

That's why I'm asking all those people who say *build-essential* is a security threat should be jumping in here, but they're not.[/QUOTE]
i actually never saw anyone claim its a security threat... the "best" excuse for this that i ever heard was that it's just there to encourage people to use the repos before resorting to building from source. which is kind of a lame excuse, i think.

i bet this policy of excluding build-essential stuff was probably borne out of some strange discussion between the packagers somewhere, and now nobody really remembers why build-essential is no longer included in the default install. :)

anyway, my vote is for including build-essential in the default install, because this comes up way too frequently on the forums.

---

### Post by HeavyAl on 2006-06-12
Not to go totally against the grain on this, but it seems to me that Ubuntu is set up for those users that want to get right into being productive only what they need to get going. Personally I build stuff left and right and love trying new things that cant be found as a package, but when it comes right down to it none of that stuff is neccesary for somebody who doesnt have a clue about linux - they just want a desktop that works, which is what Ubuntu gives you.

So, I'm not saying it should or shouldnt be in the initial install, but at the end of the day if you are a 'power user' then adding the build tools really isnt that much of a hardship is it?

---

### Post by taurus on 2006-06-12
[QUOTE=HeavyAl]
So, I'm not saying it should or shouldnt be in the initial install, but at the end of the day if you are a 'power user' then adding the build tools really isnt that much of a hardship is it?[/QUOTE]
If you know you need build-essential before you can build anything.  Most people when they migrate from other Linux distros, they always think there is something wrong with Ubuntu because they couldn't build whatever program they want because they get an error message in return about no make or can't find gcc...  Have you scanned around the forums because this is probably the most post question around here?

---

