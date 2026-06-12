---
title: "profile.local problems"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by madeupname on 2007-07-19
I modified my profile.local file to change my path to include my cross-compilers and toolchain.  Things were working fine until yesterday.  Now my path additions are no longer showing up in my path.  The profile.local is still there in /etc and still has my exports.  I can only assume that profile.local is no longer being called and/or run.

I did connect my system to the Internet and it downloaded and installed a couple updates.  I do not recall making any tweaks to anything the first time other than in profile.local so what kind of update would stop the profile.local from being used?????

Confused,

Bill

---

### Post by ihristov on 2007-07-19
I might be wrong here, but in principle isn't /etc/profiles the wrong place for adding paths?

My understanding is this is only for system wide changes.

You want to modify .bashrc in your home folder to add more folders for the compiler. Something like

export PATH=$PATH:/mypath/bin

P.S. This of course assumes you are using bash and not some other shell

---

### Post by madeupname on 2007-07-19
As far as I am concerned setting your path or environment variables for cross-compilers should be system wide. Ubuntu seems to be different than most other distributions in this regard.  (At least from the amount of mass confusion I see inferred from all the forum posts about setting paths and environment variables).  After all thinking that I only want things defined while I am in a bash shell only seems odd to me.

Anyway, my main question was why my profile.local stopped doing what it was doing rather well for weeks?

I had things set up nicely and poof they quit working today.  By the way if you read the comments in .bashrc it specifically says this is a BAD place for this because this file is subject to change during system updates and you may loose your customization.  .profile.local should on the other hand be safe.... at least in all other distributions I have worked with.

There are more than one way to skin a cat and I'm sure I can get this to do what I want, but why is Ubuntu so bass-ackward different from everything else??????

Frustrated again..... Thanks for your reply.  It seems many in the Ubuntu community think this belongs in bashrc I very much disagree.

Bill

---

### Post by ihristov on 2007-07-19
Well, maybe you are correct. But I don't see why a package installation would be manipulating files in my home folder.

However I am now confused. Where are your settings? in /etc/profiles.local or in ~/.profile.local

As far as I can see in Ubuntu 6.10 the order of invocation seems to be
/etc/profile
which loads /etc/bash.bashrc

and only then 
~/.bash_profile
which loads ~/.bashrc

I do not see use of /etc/profiles.local or ~/.profile.local

As far as the changes you suffered:

1. What version of Ubuntu are you running?

2. Take a look at the list of the updated packages in Synaptic/History to see which packages were updated and from there see a list of the files that belong to a package. Maybe you can spot the package that changed one of the files

3. As far as I know Ubuntu follows the Debian conventions so it should not be different than Debian.

4. If there is some change in this there better be a good reason for it. I cannot think of one, but I suspect you would find a thread that discusses the issue on the developers mailing list.

Again I am no expert, just a user. Maybe you can post on the developers mailing list for the affected package or post a bug on Launchpad

Also, maybe this thread is not right for the "Absolute Beginner Talk" forum. Most beginners do not compile applications now a days.

---

### Post by ihristov on 2007-07-19
> **madeupname said:**
> It seems many in the Ubuntu community think this belongs in bashrc I very much disagree.

Maybe the best approach is to place your settings in a custom file and make sure that /etc/profile (or ~/.bash_profile) include it.

---

### Post by madeupname on 2007-07-19
OK, thanks for you replies.  Despite what it might sound like I am not trying to go against the grain here, I want to do things the "Ubuntu way" whether I agree or not.  After all if I try to swim up stream I may wind up fighting Ubuntu every step of the way and I am already discombobulated.

When things don't work the way I'm used to and the threads here show 4 or 5 different answer to the same question I have a tough time trying to sort out what truly is the "best way"

So I would like to ask one more favor out of someone and look at what is now my bash.bashrc file.  I don't know if I paid much attention to it before so I don't know if it changed or by how much during the last "update", but I do know that it is SIGNIFICANTLY different and much SMALLER than the exact same file on SuSE.

______________________________________________________________________________________
______________________________________________________________________________________

Please compare it with yours and see if it looks OK or if it may be corrupt.... or incomplete:

# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/bin/command-not-found ]; then
	function command_not_found_handle {
                /usr/bin/command-not-found $1
                return $?
	}
fi

---

### Post by ihristov on 2007-07-19
I have no doubts the /etc/bash.bashrc file would be quite different between Ubuntu and Suse. That in itself is not a problem or a reason to think it was changed recently. Mine is exactly the same as the one you posted.

In which file did you make the changes that stopped working?

---

### Post by madeupname on 2007-07-19
My exports were in profile.local and they were being "sourced" and properly set until this morning.  I can force them to be set and I am not in a bind.  I am just trying to figure out the most appropriate way to do this upon boot-up and/or login (and not necessary only when I launch a bash shell)  in Ubuntu and I am also even more interested to know what happened.  Other things apparently changed as well like my color coding of files within the bash shell.  These are just two things I've noticed so far and wonder what else may have changed that I am not aware of yet.

In any even I am chugging along cross compiling libiconv, gettext and glib so I can eventually (with a little luck) port finch (Instant messenger) to an embedded product using uClinux I should do as you suggest and try to track the on-line updates that the package manager installed last night, since this is almost certainly the culprit of the whole ordeal.

What I'm doing may not be "absolute beginner" stuff, but this environment configuration issue I thought was basic enough to belong on this  thread.  I apologize if I made the wrong choice.

Bill

---

### Post by madeupname on 2007-07-25
I put my exports in bash.bashrc at the bottom and all is well. This is a little different than what I was used to but it seems like the easiest and perhaps the best solution for Ubuntu. This will be problematic if I need this path set while I am somewhere other than a bash shell, but I will cross that bridge when I come to it.

---

