---
title: "Terminal Help"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Dave85 on 2007-08-03
Hi

I&#8217;m fairly novice when it comes down to linux so please bare with me. I've been trying to create shell files to start up tomcat from the desktop (just like .bat files on windows) but in doing so, I have kinda messed up the terminal.
I changed the command section on the profile of the terminal. Now every time i try and startup the terminal, it pops up for about half a second trying to run the command and then disappears, so now i cannot use the terminal.

Is there a file that i can change the profile back to the default?

Any help will be greatly appreciated

Many Thanks

---

### Post by p_quarles on 2007-08-03
When you say that you changed the command, do you mean that you changed the command that launches the terminal from the icon? Or did you create a script or an alias? Tell us exactly what you changed and how, and someone can help you change it back.

---

### Post by Dave85 on 2007-08-03
well, i can't exactly remember what i did because i can't go back and see what i did. But under the terminal, there is an option called 'Edit profile' (i beileve) and here, there was a 'Command' field, and thats where i added something. I was hoping there is a file that stores all the profile detials, and i can manually edit this to restore it, but i cant seem to find it.
I believe the command field is what the terminal is trying to run when you run the terminal program.

I hope this helps.

---

### Post by p_quarles on 2007-08-03
Okay, I think I see what you mean. A couple things to try (I'm assuming your using Gnome, so if you're not, the commands will be different):

1) Right-click on the desktop, select "create launcher," and in the command field type "gnome-terminal." This should be a temporary fix; if it works, it will run the terminal without the profile you created. 

2) The file you're looking for is most likely /home/username/.profile  Check the contents of that. This file also lists a couple of other files that might be present (but are not, by default) -- look for those in the home directory, and check their contents if they exist.

---

### Post by Dave85 on 2007-08-03
I am using Gnome, but unfortunately, the first option doesn&#8217;t work, i presume that when I try and run the gnome-terminal from the launcher, its still looking at the same profile and doesn&#8217;t load up.

Now, for your option two, theres a file called .bash_profile which talks about a file .bashrc. But I can&#8217;t seem to understand these files. I can't spot the command I entered to remove it, or anything to say how the file works. if it's easier, I can paste the content of the files?

Thanks for your help

---

### Post by p_quarles on 2007-08-03
Yeah, post the contents of .bash_profile

That's one of the files it looks for before loading the ~/.profile settings, and therefore likely where the problem lies.

---

### Post by Dave85 on 2007-08-03
the .bash_profile content looks like this:

```

# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

export JAVA_HOME=/usr/lib/jvm/java-1.50-sun-1.5.0.08

```

It doesnt look that big so im not sure what could be wrong in this file.

Any ideas?

---

### Post by p_quarles on 2007-08-03
It's not a long file, no, but it doesn't need to be to mess things up.

Is there anything in there that reminds you what you may have added to the profile? I'm looking at the last line, especially. I have no idea why an invocation of Java would be in a bash profile.

That said, you coud try this: rename ~/.bash_profile to something else, like backup_profile  If bash_profile doesn't exist, the Gnome terminal uses ~/.profile to load.

---

### Post by Dave85 on 2007-08-03
theres nothing in that file that resembles the command that i entered. I entered the command of something like '/cd <dir>', so i think its running that when i run terminal, and ocne it does that, it shuts down. 

I tried renaming  that .bash_profile, the same problem occurs, does that mean its something in the .profile (etc/.profile)?

---

### Post by p_quarles on 2007-08-03
Maybe. If you post it, I'll take a look.

---

### Post by apswartz on 2007-08-03
There is nothing wrong with the file you posted. The line about Java simply exports a system variable that allows programs to find where Java is installed.

Try pressing Alt-F2 and type in xterm and press enter.
What happens?

---

### Post by Dave85 on 2007-08-03
the .profile file looks like this:
```

# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

```

the .bashrc file (which seems to be pointed at often) is as follows:
```

# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi


```

Any ideas from these?

@apswartz

if i do that, it does bring up some kind of terminal (which is great for a short term solution, but for a long term solution, ideally, i would like to be able to use the gnome-terminal program.

---

### Post by apswartz on 2007-08-03
Yes, but since it works that means there is nothing wrong with any of the profile or bash rc files. The problem is specific to gnome-terminal and with its settings.

Since I don't use gnome, I don't know what file those are kept in.

---

### Post by p_quarles on 2007-08-03
I'm still not seeing anything. 

The .profile file I meant, though, is the one in your home directory, not the one in /etc. Can you post that one too?

---

### Post by apswartz on 2007-08-03
> **apswartz said:**
> Yes, but since it works that means there is nothing wrong with any of the profile or bash rc files. The problem is specific to gnome-terminal and with its settings.

Since I don't use gnome, I don't know what file those are kept in.

THIS is where you want to look...
```
cd ~/.gconf/apps/gnome-terminal/profiles
```

The profiles are stored in xml files.

---

### Post by Dave85 on 2007-08-03
@ apswartz

ok thanks, at least we know its none of those bash files.

@p_quarles

there is no file just called .profile under the home folder, only .bash_profile.

So does anyone know where the setting/profile files are for gnome-terminal?

---

### Post by Dave85 on 2007-08-03
ah thanks apswartz, just saw your post, will look now :)

---

### Post by p_quarles on 2007-08-03
Good call, apswartz. The gnome-terminal documents weren't particularly forthcoming wth that information.

The profile isn't particularly readable. Posting yours might point to a solution, but if not I can post the default profile in my account, and then you see if that works.

---

### Post by apswartz on 2007-08-03
Just rename it something like profile.xml.OLD and gnome-terminal should create a new one when it starts up.

```
 mv existingprofilename profile.xml.OLD 
```

Replace the **existingprofilename** with the actual and exact name of the profile file.

---

### Post by Dave85 on 2007-08-03
ok, i found the xml profiles and if you look below, i can spot the command i entered thats causing it to not run:

```

<?xml version="1.0"?>
<gconf>
        <entry name="visible_name" mtime="1186060824" type="string">
                <stringvalue>startup</stringvalue>
        </entry>
        <entry name="update_records" mtime="1186060819" type="bool" value="false">
        </entry>
        <entry name="custom_command" mtime="1186060813" type="string">
                <stringvalue>cd /home/xxxxxx/downloads/apache-tomcat-6.0.13/bin</stringvalue>
        </entry>
        <entry name="use_custom_command" mtime="1186060786" type="bool" value="true">
        </entry>
        <entry name="palette" mtime="1186060752" type="string">
                <stringvalue>#000000000000:#AAAA00000000:#0000AAAA0000:#AAAA55550000:#00000000AAAA:#AAAA0000AAAA:#0000AAAAAAAA:#AAAAAAAAAAAA:#555555555555:#FFFF55555555:#5555FFFF5555:#FFFFFFFF5555:#55555555FFFF:#FFFF5555FFFF:#5555FFFFFFFF:#FFFFFFFFFFFF</stringvalue>
        </entry>
</gconf>

```

so, i went into txt editor to change it, so i changed it to this:
```

<?xml version="1.0"?>
<gconf>
        <entry name="visible_name" mtime="1186060824" type="string">
                <stringvalue>startup</stringvalue>
        </entry>
        <entry name="update_records" mtime="1186060819" type="bool" value="false">
        </entry>
        <entry name="palette" mtime="1186060752" type="string">
                <stringvalue>#000000000000:#AAAA00000000:#0000AAAA0000:#AAAA55550000:#00000000AAAA:#AAAA0000AAAA:#0000AAAAAAAA:#AAAAAAAAAAAA:#555555555555:#FFFF55555555:#5555FFFF5555:#FFFFFFFF5555:#55555555FFFF:#FFFF5555FFFF:#5555FFFFFFFF:#FFFFFFFFFFFF</stringvalue>
        </entry>
</gconf>

```

So thats what i asume is the basic code for the default file, but yet, when i try and run gnome, it does the same thing and won't load!

Have i forgotten anything?

---

### Post by Dave85 on 2007-08-03
just tried re-naming the file aswell, gnome-terminal still won't load up properly.

---

### Post by p_quarles on 2007-08-03
Those other "entry name" lines might have been added when you customzied it. For comparison, here's my profile:
```
<?xml version="1.0"?>
<gconf>
        <entry name="palette" mtime="1186157245" type="string">
                <stringvalue>#000000000000:#AAAA00000000:#0000AAAA0000:#AAAA55550000:#00000000AAAA:#AAAA0000AAAA:#0000AAAAAAAA:#AAAAAAAAAAAA:#555555555555:#FFFF55555555:#5555FFFF5555:#FFFFFFFF5555:#55555555FFFF:#FFFF5555FFFF:#5555FFFFFFFF:#FFFFFFFFFFFF</stringvalue>
        </entry>
</gconf>
```

---

### Post by apswartz on 2007-08-03
Actually, you can just delete the whole profile directory. When you restart gnome-terminal everything should be fine and new profiles will be created as needed.

```

cd ~/.gconf/apps
rm -fR gnome-terminal

```

Then Alt-F2 and run gnome-terminal

---

### Post by p_quarles on 2007-08-03
> **Dave85 said:**
> just tried re-naming the file aswell, gnome-terminal still won't load up properly.
Well, if that didn't work, changing the profile settings probably won't either. 

Just to be sure, try this (alt-F2):
```
gnome-terminal --window-with-profile=*fakeprofile*
```
Use whatever profile name, as long as it doesn't exist. 

For what it's worth, if you can run xterm, you're fine. The Gnome terminal emulator is the same thing, for most purposes. It's integrated a little more tightly with Gnome settings, but other than that it's no different.

---

### Post by Dave85 on 2007-08-03
yep, your right, deleting the profile files didnt work either so i take it its nothing to do with the profiles either :S this is werid. I guess xterm will work, but terminal just seemed tidier and neater.

If you have any other ideas what could be causing it, i would love to hear them, otherwise Many thanks for both your help.

---

### Post by p_quarles on 2007-08-03
I suppose you could try this:
```
sudo dpkg --configure gnome-terminal
```
That will try to restore the original settings.

---

### Post by Dave85 on 2007-08-03
that brings up an error stating that gnome-terminal has already been installed and configured!

hmmmm

---

### Post by apswartz on 2007-08-03
You know it really bothers me that it is so hard to find where those user changes are stored.

---

### Post by apswartz on 2007-08-03
Found it!

Press Alt-F2 and run gconf-editor
Under apps, select gnome-terminal and then you can search for and delete the offending entries.

<sarcasm>shades of Windows Registry</sarcasm>

---

### Post by p_quarles on 2007-08-03
> **apswartz said:**
> Found it!

Press Alt-F2 and run gconf-editor
Under apps, select gnome-terminal and then you can search for and delete the offending entries.

<sarcasm>shades of Windows Registry</sarcasm>
Agreed. I love Gnome, but gconf editor is definitely out of step with the way everything else in Linux works. 

I just looked at the terminal profile using that method, and it appears to be the same as the file you pointed out earlier. Of course, the config file failed the human-readable test, so I'm not sure.

@Dave85: Try the following. It'll return the status of the package:
```
dpkg -s gnome-terminal
```

---

### Post by asmoore82 on 2007-08-03
> **apswartz said:**
> Actually, you can just delete the whole profile directory. When you restart gnome-terminal everything should be fine and new profiles will be created as needed.

```

cd ~/.gconf/apps
rm -fR gnome-terminal

```

Then Alt-F2 and run gnome-terminal

this step fixed your problem beyond a shadow of doubt, but you need to logout
and back in again immediately after this step.

gconf has some new cached state mechanics that i'm not yet familiar with.

P.S. actually come to think about it, gconf could've been behaving this way for a long time
and I wouldn't have known; I usually fix little hiccups like this in a failsafe term session.

---

### Post by asmoore82 on 2007-08-03
getting back to your original intentions ...

the most proper way to do create these launcher scripts would be to save them
as executable bash shell scripts in a central location ...
like a "bin" folder or hidden ".bin" folder in your home directory.
then make simple "Custom Launchers" on your Desktop that call these scripts.

this is how I start my VirtualBox OSE ...

```

asmoore@asmoore-laptop:~$ ls bin/
**VirtualBox**
asmoore@asmoore-laptop:~$ cat bin/VirtualBox 
#!/bin/bash

me="${0##*/}:"
vruntime="$HOME/src/VirtualBox-OSE-1.4.0/out/linux.x86/release/bin"

if [ ! -d "$vruntime" ]; then
        echo "$me" "Virtual Box OSE Runtime Not Found ... Aborting." 1>&2
        exit 1;
fi

cd "$vruntime"
export LD_LIBRARY_PATH=.
./VBoxSVC &
sleep 2
./VirtualBox
sleep 2
kill %%
wait

#End of File
asmoore@asmoore-laptop:~$ cat Desktop/VirtualBox\ OSE.desktop 

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=true
Name[en_US]=VirtualBox OSE
Exec=/home/asmoore/bin/VirtualBox
Icon[en_US]=/usr/share/pixmaps/tsclient.png
Name=VirtualBox OSE
Icon=/usr/share/pixmaps/tsclient.png
```

---

### Post by Dave85 on 2007-08-03
Fantastic, logging out and then back in did the trick!

Many thanks to all three of you for helping me sort this out. I greatly appreciate it.

Dave :)

p.s. @asmoore82: thanks for the help with the shell scripts, after i caused this issue, i stopped looking at how to do them.

---

