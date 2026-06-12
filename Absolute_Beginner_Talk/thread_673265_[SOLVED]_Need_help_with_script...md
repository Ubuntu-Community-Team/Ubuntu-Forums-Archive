---
title: "[SOLVED] Need help with script.."
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by trooperchix on 2008-01-20
I am attempting a fix I found for dual core processor systems and Neverwinter Nights.  

The link for all the instructions is: 

[http://nwn.bioware.com/forums/viewtopic.html?topic=484346&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=484346&forum=72)

Anyway, the last bit (in red)  I don't know how to do.  Could someone help me?  I'd appreciate it...
                 ***
This is the short version.. ( And it will very much depend on you having all the appropriate development packages installed, since unfortunately, I don't see a pre-built binary for Ubuntu... )

I hope you're at least a little familiar w/ the command line.

    Code:

    mkdir /tmp/run
    cd /tmp/run
    wget [http://ccur.com/oss/run-3.0.tar.gz](http://ccur.com/oss/run-3.0.tar.gz)
    gzip -d -c run-3.0.tar.gz | tar xvof -
    cd run-3.0
    ./configure --disable-shared
    make

[COLOR="Red"]Once the ./configure, and make complete you should have a run binary in /tmp/run/run-3.0/run
Copy it somewhere in your PATH and edit your nwmain script.

$HOME/bin should be in your path, and shouldn't require root to write to.

Try to pay attention to the output of the ./configure and see if it does, (or doesn't whine) loudly about missing things.

David[/COLOR]
        ***
Thanks again...

---

### Post by frup on 2008-01-20
did you need to do make install?

gzip -d -c run-3.0.tar.gz | tar xvof -

try put sudo in front of that part if the  run-3.0 folder is not being made. /tmp is owned by root so you can't exactly write to it without sudo.

---

### Post by cmnorton on 2008-01-20
> **trooperchix said:**
> I am attempting a fix I found for dual core processor systems and Neverwinter Nights.  

The link for all the instructions is: 

[http://nwn.bioware.com/forums/viewtopic.html?topic=484346&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=484346&forum=72)

Anyway, the last bit (in red)  I don't know how to do.  Could someone help me?  I'd appreciate it...
                 ***
This is the short version.. ( And it will very much depend on you having all the appropriate development packages installed, since unfortunately, I don't see a pre-built binary for Ubuntu... )

I hope you're at least a little familiar w/ the command line.

    Code:

    mkdir /tmp/run
    cd /tmp/run
    wget [http://ccur.com/oss/run-3.0.tar.gz](http://ccur.com/oss/run-3.0.tar.gz)
    gzip -d -c run-3.0.tar.gz | tar xvof -
    cd run-3.0
    ./configure --disable-shared
    make

[COLOR="Red"]Once the ./configure, and make complete you should have a run binary in /tmp/run/run-3.0/run
Copy it somewhere in your PATH and edit your nwmain script.

$HOME/bin should be in your path, and shouldn't require root to write to.

Try to pay attention to the output of the ./configure and see if it does, (or doesn't whine) loudly about missing things.

David[/COLOR]
        ***
Thanks again...

1) The ./ prefix is added to configure, because, more than likely, temporary build directory is not in your path. ./ says essentially run this from here (pwd).

2) Enter make, and make sure everything built correctly.

3)  Enter ls -ld ~/bin

If there is no bin directory, create one (mkdir ~/bin), and place the nwmain script into your bin directory. Your instructions say copy this somewhere in your PATH. Don't forget to set the executable bit chmod +x bin/nwmain

If you create a bin directory inside your home directory, .bash_profile should already have this in it:


# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
. ./.bashrc

That would put bin in your PATH environment variable.

---

### Post by trooperchix on 2008-01-20
> **cmnorton said:**
> 1) The ./ prefix is added to configure, because, more than likely, temporary build directory is not in your path. ./ says essentially run this from here (pwd).

2) Enter make, and make sure everything built correctly.

3)  Enter ls -ld ~/bin

If there is no bin directory, create one (mkdir ~/bin), and place the nwmain script into your bin directory. Your instructions say copy this somewhere in your PATH. Don't forget to set the executable bit chmod +x bin/nwmain

If you create a bin directory inside your home directory, .bash_profile should already have this in it:


# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
. ./.bashrc

That would put bin in your PATH environment variable.

Ok, I understood the first two steps and competed half of the third.  I didn't have a bin directory, so I created one.  The paths of my files are /home/eddie/games/nwn  and /home/eddie/bin  and my terminal prompt sits at: eddie@dell:/tmp/run/run-3.0$ 

I'm starting to get this, any ideas on what I should read, etc to learn this stuff?  I'm hands down a die hard convert, my poor Vista system sits gathering dust...  

Oh, and thanks ahead of time...

---

### Post by trooperchix on 2008-01-20
Can anyone please help me through this last bit?  

Thanks.

---

### Post by cmnorton on 2008-01-21
The third step I wrote was to show that putting the script into your bin directory put it into your PATH environment variable, because bin is put into your PATH for you in .bash_profile.

There are many good scripting books; Ken O. Burtch's Linux Shell Scripting with Bash and O'Reilly's Linux in a Nutshell and Learning the Bash shell are pretty good.  [www.die.net](www.die.net) isn't bad either.

I'm missing your other question. I could not figure it out from your post.

---

### Post by trooperchix on 2008-01-21
OH, ok, what I was looking for is the actual script I need to run for step 3.  The whole # PATH thing has me lost.  Would you be willing to write the code for it?  I'm completely clueless...

---

### Post by cmnorton on 2008-01-21
You don't have to adjust your PATH environment variable, if you 

a) Put the shell script into /home/<your_home_directory>/bin, where <your_home_directory> is the top level directory of the user login who will be running this shell script.

b) Make sure you set executable mode on the shell script -- chmod +x -- /home/<your_home_directory>/shell_script_in_question

The reason you do not need to alter your PATH is because the .bash_profile script has already done this for you.

---

### Post by trooperchix on 2008-01-21
Alright, I'm going to run home and figure out if this works.  So, if I am understanding you correctly, I need to do step 2 and nothing else.  I don't have to modify nwnmain or anything?  What would be my "shell_script_in_question"
I love you man!!   :guitar:

b) Make sure you set executable mode on the shell script -- chmod +x -- /home/<your_home_directory>/shell_script_in_questi on

so it would be

-- chmod +x-- /home/booger/[COLOR="Red"]???[/COLOR]

---

### Post by trooperchix on 2008-01-21
Oh wait, figured that out...

Now, how do I look at my .bash_profile script?  I don't see it.  I just want to make sure I have everything set up right.   I'm going to try and run NWN and see if it plays well with others...

---

### Post by bodhi.zazen on 2008-01-21
It is a hidden file in your home directory.

gedit ~/.bash_profile

---

### Post by trooperchix on 2008-01-23
I don't see anything in my .bash_profile so what script do I need to put in there?  Also, the run program, I have it in my tmp file, but it says to move it somewhere and to edit my nwmain script?  Um, no clue.  I see what has to be done, but have no clue how to do it.  Any further help out there would be lovely...  Lady Aribeth awaits!!

---

### Post by trooperchix on 2008-01-27
Ok, pulled my head out.  I get it now.  I don't think the fix is working though.  I'll keep looking for a fix on this.  thanks for all your help guys.  :)

---

