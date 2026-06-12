---
title: "Install latest Mono from binary installer"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by flipm0de on 2007-12-13
Hello all,
First I want to thank everybody on the Ubuntu team for the great work, and the beautifill distribution that they have created.
Now to te point. I am developing an open source application (GPL) that needs the latest version of mono installed on the machine. I am recomending people to use Ubuntu as i is one of the easiest distributions for instalation and work for people with no or limited technikal knowledge (and there are a lot of them). I am also trying to write a HOWTO install the latest mono from a binary installer to Ubuntu. So far I have reached the point where I can install the latest version (in /opt/mono-1.2.x) and resolve all the dependances for my software and mono.
The only part left AFAIK is to modify the gdm environment variables so that the proper mono runtime is being used when a the user is trying to execute my software from a launcher. The environment varialbles that need to be modified are mentioned here[ http://www.mono-project.com/Parallel_Mono_Environments]("http://www.mono-project.com/Parallel_Mono_Environments") and are something like:

export PATH="/opt/mono-1.2.6/bin:$PATH"

export PKG_CONFIG_PATH="/opt/mono-1.2.6/lib/pkgconfig:$PKG_CONFIG_PATH"

export MANPATH="/opt/mono-1.2.6/share/man:$MANPATH"

export LD_LIBRARY_PATH="/opt/mono-1.2.6/lib:$LD_LIBRARY_PATH"

Can somebody please point me to the right place to place this? I tried /etc/environment but no luck. I am trying to make the new version of mono available system wide.

Thanks
 Vladimir

---

### Post by swheatley on 2007-12-21
Vladimir: Just following up to see if you had any luck with this. As a recent convert from Windows, I'm desperate to try Paint.NET (I don't really care for the GIMP, and Paint.NET is open source as well). However, it to requires the latest Mono (1.2.6). Please let me know when you find the best way to achieve this.

---

### Post by emperon on 2007-12-22
put those variables to a file and call with

source <your_file>

and now you are in the parallel environment. you have to do this everytime you need your new mono

---

