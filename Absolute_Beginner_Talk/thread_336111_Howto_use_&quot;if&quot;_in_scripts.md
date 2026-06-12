---
title: "Howto use &quot;if&quot; in scripts ?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Ecthelion on 2007-01-11
Hey,

I'm trying to make a little script and I just can't find how to use "if".
What is the correct syntax?
There is no manual page etc...

What I would like to do is a little script to check if beryl is on.
If it's on, then the script should replace it with metacity.
If beryl is not on, then the script should start it up.

I know how to Enable/Disable beryl in command line.
What I don't know is how to put in a command that get's executed if correct, and not if wrong.

So what I more or less have is this:
> 
ps -A|grep "beryl-manager"; *****
if ******
killall beryl-manager;
metacity --replace;
elif *******
beryl-manager;
emerald --replace;


*****
Here I need a command that saves the output. I know I could use "* ps -A|grep "beryl-manager" > log *" but that would make a extra file. Can it be saved otherwise?

******
If "beryl-manager" is found running, then this should be executed.
Is there a way to compare two Strings and get the answer true or false? (in normal commandline syntax?)
(I can program a bit in Java, but that's it. I'm rather a beginner)

*******
I'm not sure this is the correct name. I guess this stands for "else if". But that not really what I need. I only need "else".
So that this gets executed if beryl manager wasn't found running.


I'm not sure if this had to be in Absolute Beginner Talk. It's rather beginner, but it could also be placed under "programming talk".
If a moderator feels it needs to be there, feel free to move it.

Tx for any answer,

Ecthelion

---

### Post by pcomelade on 2007-01-11
Try something like this:

if ps -A | grep "beryl-manager" > /dev/null 
    then 
       killall beryl-manager;
       metacity --replace;
else
       beryl-manager;
       emerald --replace;
fi


Hope it helps

M;

---

### Post by Ecthelion on 2007-01-11
> Hope it helps

Yes it did. :D

I just have one question left...
> if ps -A | grep "beryl-manager" > /dev/null 
What does this exactly do?
Am I right if I think this compares the output of grep with /dev/null ?
So that if this is false, then it means that something was found (and that it wasn't a "null" output).


For other people who might want to use this script, it is not needed to do "emerald --replace".
When beryl-manager starts up it usually replaces it automatically.
So the script looks like this.

> if ps -A | grep "beryl-manager" > /dev/null
then
killall beryl-manager;
metacity --replace;
else
beryl-manager;
fi

@pcomelade  => thanks for your help :KS

---

### Post by pcomelade on 2007-01-11
> if ps -A | grep "beryl-manager" > /dev/null

The output of "ps -A | grep "beryl-manager" is redirected (>) to /dev/null (a special device that silently ignores it), This is done because you are not interested in the output of this command, you only want to know the "exit status" of the command, that is "true" if grep finds "beryl-manager".
This "true" signal makes the "if" statement to execute the code.

cheers!

M;

---

### Post by Ecthelion on 2007-01-11
> The output of "ps -A | grep "beryl-manager" is redirected (>) to /dev/null (a special device that silently ignores it), This is done because you are not interested in the output of this command, you only want to know the "exit status" of the command, that is "true" if grep finds "beryl-manager".
This "true" signal makes the "if" statement to execute the code.

Oh allright.
Didn't knew about an exit status.
I knew the /dev/null ignores it, so I though a true would mean there was nothing to ignore...
Well I certainly learned something!

Thanks for the help!

---

### Post by Ecthelion on 2007-01-12
Other question...

Can you give options when starting a script?
For example:
Let's assume that I have a script called "Script" 8) 
Is it then possible to do for example
```
./Script **3**
```
Where 3 is an option that is configured in the script.

How would this option "3" have to be implemented in that script?

The reason why I ask this is because there are a lot of commandos with options...
f.e.: the "ps -A" used earlier
The -A is an option... Can this kind of option be implemented in scripts too...? How?

Thanks for helping this far :-)

---

### Post by seuaniu on 2007-01-12
> **Ecthelion said:**
> Other question...

Can you give options when starting a script?


You sure can.  BASH will assign any command-line arguments to the variables $1, $2, etc, so you can reference them like:

```


if $1 = "--help" 
then
    echo "insert help message here"

else
    ...
    ....

fi

```

but check the manpage for the proper syntax, since I really haven't written a script in awhile ;)  While you're at it, check out the -n argument to echo.  You can use that to have your script ask for user input, assign a variable to that input, and use it however you want.  This makes for interactive scripts, which might be helpful.

---

### Post by Ecthelion on 2007-01-12
So if this would be my script:
> 
if $1 = "-ON"
then
beryl-manager;
elif $1 = "-OFF"
then
killall beryl-manager;
metacity --replace;
elif ps -A | grep "beryl-manager" > /dev/null
then
killall beryl-manager;
metacity --replace;
else
beryl-manager;
fi


Then I could use this scipt to on / off beryl if I have no option, and, for example when I want to play tremulous, also use this script:
> 
if ps -A | grep "beryl-manager" > /dev/null
then
./Scrip -OFF;
tremulous --quiet;
else
tremulous --quiet;
fi

This is not a real good example since I could've typed the whole script again, but it's just to see if I get it right...

The thing I wondered when I read 
> You sure can. BASH will assign any command-line arguments to the variables $1, $2, etc, so you can reference them like:
was:
If I implement two different kind of options in my script. Let's say option -ON and option -S.
To put it in an example:
The option -ON gets used as in my previous example, the option -S determines if there is a splash screen when beryl starts up.
If I then give as command
```
./Script -ON -S
```
or
```
./Script -S -ON
```
Do these options get saved to different numbers?
I ask this because if -S gets saved to $1, then the "*  if $1 = "-ON"  *" would be false even if the option "-ON" WAS given...
Or is there a smart way around this problem?

---

### Post by seuaniu on 2007-01-12
This gets a little advanced, and to be quite honest, a bit over my head.  But, you'll probably want to write a function to parse all of your options, check that they aren't in conflict with each other (like if you do a ./script on off), and try to be smart about how they are handled.

Here's a good bash tutorial.
[http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)

Also, check out some of the scripts that are already on your machine.

Here's an example pulled from /usr/sbin/chkrootkit on my debian server:

```

### default ROOTDIR is "/"
ROOTDIR='/'

while :
do
        case $1 in
        -r)     shift
                ROOTDIR=$1;;

        -p)     shift
                CHKRKPATH=$1;;

        -d)     DEBUG=t;;

        -x)     EXPERT=t;;

        -q)     QUIET=t;;

        -V)     echo >&2 "chkrootkit version ${CHKROOTKIT_VERSION}"
                exit 1;;

        -l)     echo >&2 "$0: tests: ${TOOLS} ${TROJAN}"
                exit 1;;

        -n)     tnfs;;

        -h | -*) echo >&2 "Usage: $0 [options] [test ...]
Options:
        -h                show this help and exit
        -V                show version information and exit
        -l                show available tests and exit
        -d                debug
        -q                quiet mode
        -x                expert mode
        -r dir            use dir as the root directory
        -p dir1:dir2:dirN path for the external commands used by chkrootkit
        -n                skip NFS mounted dirs"
                exit 1;;
        *)      break
        esac

        shift
done

```

---

### Post by Ecthelion on 2007-01-12
I've already bookmarked the tutorial... Sure gonna follow it!

Also, good hint!
I'll look to some of the scripts on my machine.

Thanks a lot for the help !!!

---

### Post by Ecthelion on 2007-01-13
I finally have a script that works as I want.
It's still a bit beginner (surely possible to simplify some of it). But it works.
If anyone would be interested, here's what I have.
=> If you think it can be improved (an you know how), please tell me how.
The more feedback, the better :-)

> #!/bin/bash
#Script made the 12/1/2007 by Ecthelion

NO_ARGS=0

if [ $# -eq "$NO_ARGS" ]  # Script invoked with no command-line args?
then
	if ps -A | grep "beryl-manager" > /dev/null;
	then 			#Shutdown Beryl
	killall beryl-manager;
	metacity --replace;
	else			#Startup Beryl
	beryl-manager;
	fi
fi 

while getopts ":O:" Option
do
  case $Option in
    O     ) 	if [ "ff" = "$OPTARG" ]    #Off option: make sure beryl is NOT running
		then
			if ps -A | grep "beryl-manager" > /dev/null;  # Is Beryl running? Then shut it down.
				then
				echo "Beryl is being shutdown";
				killall beryl-manager;
				metacity --replace ;
			else                                                                           # Beryl was not running: do nothing.
				echo "Beryl is not running"
			fi
		elif [ "n" = "$OPTARG" ]  # "On" option: You want to make sure Beryl runs
		then
			if ps -A | grep "beryl-manager" > /dev/null;     # Is Beryl running? => yes: do nothing.
                        then
				echo "Beryl is already running"
			else                                                                             # Beryl is not running: start up.
				echo "Starting up Beryl";
				beryl-manager;
			fi
		else
		echo "Wrong input, possible options are  -On / -Off";  #Wrong input
		#echo "You input was \"$OPTARG\" ";
		fi ;;
    *     ) echo "Unimplemented option chosen." ;;   # DEFAULT
  esac
done
exit 

Too bad you can't put structure in a quote. When I see how it looks in this post I don't understand half of it myself.
Really more readable when you can put blank space in front of commands...

I want to thank seuaniu and pcomelade for their help!

---

### Post by Ecthelion on 2007-01-15
There are still some problems on the script.

Since this starts to grow off-topic (not really related to howto use if...), I started a new thread:
[http://ubuntuforums.org/showthread.php?p=2015148](http://ubuntuforums.org/showthread.php?p=2015148)

Please help me to finish this script :KS 

Ecthelion

---

