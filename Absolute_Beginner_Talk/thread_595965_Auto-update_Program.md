---
title: "Auto-update Program"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Obfuscater on 2007-10-29
*clears throat* Hello.

I'm very new to linux (don't ask me what I was waiting for; I don't know), having used it for about 2 days now, on and off. 

I've got the install set up and I'm looking into nameserver setups so I can host from home in style. By the way, as you all know, Linux is amazing. Really, really amazing.

Anyway, that's all by the bye.

I figured that since I will no doubt be crying out for help regularly on this forum the polite thing to do would be offer a program to you all in the spirit of opensource development. So, here goes:

This Program will auto-update the software on your Linux computer and clean up any outdated install files. 
Please note that the beginner instructions do advise that you do not download the most recent version of programs, so if a more experienced user would like to modify the code to be in keeping with that advice I would welcome it.

```
#!/bin/bash
## Update all software on the box and then remove outdated install files.
## Uses the aptitude [command] functions
# List paramaters
function usage
{
echo "-h | --help -> This command output"
echo "-d | --update -> Update software libraries"
echo "-g | --upgrade -> Upgrade software"
echo "-c | --clean -> Autoclean outdated install files"
exit 0;	
}

# Body
echo "-- Update, Upgrade, Clean Program --"
	# Check for Superuser Authority	
	if [ "$(id -u)" != "0" ] ; then
		echo "Only Superusers may execute this script.">&2
		echo "-- UPDATE, UPGRADE, CLEAN process ABORTED --"
	exit 1;
	else
	# Check parameters
		if [ $# != 0 ]; then
		while [ "$1" != "" ]; do
			case $1 in
			-h | --help ) usage;;
			-d | --update ) aptitude update; shift;;
			-g | --upgrade ) aptitude safe-upgrade; shift;;
			-c | --clean ) aptitude autoclean; shift;;
			* ) echo "No valid command issued; executing 'help' message:">&2; usage;;			
			esac
		done
		exit $?
		else	
		# Print Menu
			echo "Menu:"
		fi
	fi
input=
until [ "$select" = 0 ]; do
	echo "1: Update software libraries."
	echo "2: Upgrade software."
	echo "3: Autoclean outdated install files."
	echo "4: All."
	echo "5: Exit."
	echo "Select a number or numbers (eg. 1, 12, 4)"
	read input
		case $input in
		1 ) aptitude update; exit $?;;
		2 ) aptitude safe-upgrade;exit $?;;
		3 ) aptitude autoclean;exit $?;;
		4 ) aptitude update; aptitude safe-upgrade; aptitude autoclean; exit $?;;
		5 ) echo "-- UPDATE, UPGRADE, CLEAN process exited --";exit 0;;
		* ) echo "Command Not Recognised";;
		esac
	done
```

To create that file somewhere you can find it again, I suggest either your home directory or the bin subfolder. Since I'm more of a command line man than a GUI one I'll give you the command line approach:

Command line approach for Ubuntu 7.10

1. Open up the console.
2. Navigate to your home directory (where you should be by default)
```
$ cd 
```
Please note that we typed "cd " rather than just "cd".
3. Use temporary superuser powers to create the file:
```
$ gksudo gedit software_update &
```
4. Copy and paste the program into the text editor, then save it and close it.
5. Set the access rights of the users for the file. We'll set it to superuser only even though the program itself checks if the user is a SU:
5a. Ensure the owner is root:
```
sudo chown root software_update
```
5b. Ensure only root can read/write/execute:
```
sudo chmod 700 software_update
```
6. Execute the file:
```
sudo software_update
```

And that's that. On my system the command is PATHed to be executable from any location, but at the moment I'm not 100% sure how that's done so I won't muddle you by offering a messy way to do it (he says having posted some throughly messy code).

Feedback, corrections, and advice appreciated. Evisceration not so much.

---

### Post by DezSP on 2007-10-29
The easiest way to get something to be executable from any directory is to have the script in your PATH somewhere (probably /usr/local/sbin/). Or you could fiddle about with your PATH variable to include some other directory, but that's not the best option unless you know what you're doing really.

---

### Post by Obfuscater on 2007-10-30
I did the latter, but, as you said, it's not advisable to muck about with it unless you're sure what you're doing so I'm not going to give potentially erroneous advice, especially being inexperienced in this environment. Thank you.

---

