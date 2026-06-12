---
title: "Making everything in a directory and its subdirectories in lowercase"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Hork on 2007-06-24
```
rename 'y/A-Z/a-z/' *
```

That code right there only renames stuff in the base of the directory.

For example, I want to rename everything in ~/thegame and its subdirectories ~/thegame/lose and ~/thegame/win to lowercase letters.

That code up there only renames stuff in ~/thegame to lowercase letters.

I'd just CD to the directories but there's like 50 sub directories.

---

### Post by Hork on 2007-06-24
Eh, bump (not sure if these are allowed!)

---

### Post by bigboy_pdb on 2007-06-25
Hork, I needed to do something similar so I figured that now would be a good time to solve this problem.

I've prepared a script that you can use to solve your problem. However, it's late where I am and I haven't had adequate time to test it and write a description of how to use it so I'll post the script and the information about it when I wake up tomorrow.

---

### Post by bigboy_pdb on 2007-06-25
This script doesn't do specifically what was requested (by Hork). It walks the subdirectories of the directory that you specify and performs the task that you specify in each subdirectory.  The section entitled 'EXAMPLES OF SCRIPT USE' specifies a few of the additional ways that the script can be used.

**THE SCRIPT**

EDIT: I made a change to the script
EDIT: I made a few important changes to the script

```

#!/bin/bash

##########
#
# Get the command that is to be executed during tree walk
#
##########

# The command to be executed was passed as an argument
if (( "$#" > 0 )); then
	EXEC_COMMAND="$1"
	
# No command to be executed was passed as an argument
# (Print message to standard error)
else
	echo "A command must be specified" 1>&2
	exit 1
fi
shift

##########
#
# Get directory that is the base directory for tree walk
#
##########

# A base directory where command is to be called was passed as a paramenter
if (( "$#" > 0 )); then
	# Path is relative
	if [ "${1:0:1}" != "/" ]; then
		BASE_DIR="$PWD/$1"
	# Path is absolute
	else
		BASE_DIR="$1"
	fi
	shift
# No base directory where command is to be called was passed as a paramenter
# (Use the current directory as the directory as the base directory)
else
	BASE_DIR="$PWD"
fi

# Current base directory does not exist
if ! [ -e "$BASE_DIR" ]; then
	echo "The directory '$BASE_DIR' does not exist." 1>&2
	exit 2
fi

##########
#
# Move to directory that was specified, perform command, and obtain subdirectories
#
##########

last=1 # Position of last directory in array dirs
i=1 # Counter for traversing array dirs
dirs[$i]="$BASE_DIR" # Array of directories the command is to be executed in

while (( $i <= $last )); do
	current_dir="${dirs[$i]/%\//}/" # Current directory with slash at end
	# NOTE: Slash at end is necessary for when current_dir is root directory
	
	# Move to current directory and attempt to execute command
	cd "$current_dir"&& \
		if ! eval "$EXEC_COMMAND"; then \
			echo "Could not execute command '$EXEC_COMMAND'."; \
			exit 3; \
		fi
	
	# Get directories in current directory
	while read line; do
		last=$((last + 1))
		dirs[$last]="${current_dir}${line}"
	done < <(ls -l "$current_dir" | grep '^d' | sed 's/^\([^ ]* *\)\{7\}//')
	
	i=$((i + 1))
done

```

**CREATING THE EXECUTABLE SCRIPT**
Make a new file called 'tw' and save the script into it. Then, open a terminal ('Applications'->'Accessories'->'Terminal') and type 'chmod 755 tw' to change the file containing the bash script so that it can be executed.

**RUNNING THE SCRIPT**
Method 1:
You must type the path to the script in order to use it
(ie. if you are in the directory it is located in use: './tw ls')

Method 2:
Copy/create a link to the script in a directory in $PATH (or add the directory it is located in to $PATH)
(ie. Copy it to /bin 'sudo cp tw /bin' and to use it: 'tw ls')

Medthod 3:
Create an alias that has the full path to the script that is named the same name as the script.
(ie. Add the following to /home/user/bash.rc 'alias tw="\"/absolutePathToScript/tw\""' and to use it open a new terminal and type: 'tw ls')

**FORMAT FOR RUNNING THE SCRIPT AND INFORMATION ABOUT IT**
The program walks the directory tree executing a command or set of commands that you specify starting in the base directory. This means that the command is first executed in the base directory, then in the subdirectories within the base directory, then in the subdirectories of the subdirectories of the base directory, and so forth. The script is executed in the following manner:

tw commands base_directory

base_directory is the directory that the tree walk starts in. If no base directory is specified then the working directory (the current directory) is used.
commands is the command or sequence of commands that you want to execute in each directory that is traversed.
NOTE: Since the directory is changed during the execution of the script, be cautious about using relative paths. 

**EXAMPLES OF SCRIPT USE**
# Print every directory found in your computer starting in the root directory

tw 'echo $PWD' /

# Remove files in your home folder ending with a ~ that are left behind from editing text files using gedit (without printing errors when no files ending in ~ are found)

tw 'rm *~' /home/user 2>&-

# Print number of files in each directory

tw 'echo $PWD; ls | wc -l'

**TESTED**
1. Use root as base directory
	tw 'echo $PWD' /
2. Use absolute path for base directory
	tw 'echo $PWD' /home/user/Desktop/
3. Use relative path for base directory
	tw 'echo $PWD' Desktop
4. Have a trailing slash in base directory
	tw 'echo $PWD' Desktop/
5. Don't specify a base directory
	tw 'echo $PWD'
6. Don't specify any parameters
	tw
7. Use commands found in one of directories found in $PATH
	tw ls
8. Use commands specified using absolute paths
	tw /bin/ls
9. Use commands specified using relative paths
	tw ../../../bin/ls
10. Use script in file it is located in
	./tw 'echo $PWD; ls | wc -l'
11. Use script by placing a link to it in a directory in $PATH
	cd /bin
	sudo ln -s "pathToScript/tw" tw
	tw 'echo $PWD; ls | wc -l'
12. Use script by creating alias that converts tw to absolute path of script
	sudo rm /bin/tw
	alias tw='"pathToScript/tw"'
	tw 'echo $PWD; ls | wc -l'
13. Use directory that doesn't exist
	tw ls nonExistentDirectory
14. Use command that doesn't exist
	tw nonExistentCommand

**WHAT THE SCRIPT WON'T DO**
* Traverse symbolic links that are linked to directories

---

### Post by muguwmp67 on 2007-06-25
There is also a utility called 'convmv' that does this.  You can install it from synaptic.

---

### Post by bigboy_pdb on 2007-06-25
In your case you should be able to execute the script using:
tw "rename 'y/A-Z/a-z/' *" directoryToBeUsedOn

Just to be safe, it might be a good idea to make a copy of the directory you're using it on, use the program on the copied directory, look it over, delete the original, and move the new one to where the original was. I've listed what I've tested the script with and if you're familiar with bash scripts then you can look it over.

---

### Post by cogadh on 2007-06-25
> **Hork said:**
> ```
rename 'y/A-Z/a-z/' *
```

That code right there only renames stuff in the base of the directory.

For example, I want to rename everything in ~/thegame and its subdirectories ~/thegame/lose and ~/thegame/win to lowercase letters.

That code up there only renames stuff in ~/thegame to lowercase letters.

I'd just CD to the directories but there's like 50 sub directories.
Not sure if rename allows this, but the "-r" option adds recursive functions to most commands. That may work for this (it works for deleting directories that aren't empty yet).

---

### Post by Gen2ly on 2007-06-25
there's also another app call pyrenamer

---

### Post by punx45 on 2007-06-25
> **cogadh said:**
> Not sure if rename allows this, but the "-r" option adds recursive functions to most commands. That may work for this (it works for deleting directories that aren't empty yet).

sadly, the man says no -r for rename.

just another example of the man (page) tryin to keep us down  ;)

---

### Post by bigboy_pdb on 2007-06-25
I made a change to the top of my post with the script that I posted. I'll reiterate it here as well.

The script that I posted doesn't just do what the person who started the thread asked for. It has a general use. It walks the subdirectories of the directory that you specify and performs the task that you specify in each subdirectory. So basically, it can do a number of things.

A few examples are:

tw 'rm *~' /home/user 2>&-

This goes through your folders and deletes files ending in a ~ (the ~ files are files that gedit leaves behind when you edit a text document). Also, it doesn't print errors when there are no files ending in tildes in a directory.

tw 'echo $PWD; ls; echo'

This lists each directory followed by the list of files within the directory followed by a blank line.

tw 'echo $PWD; ls | wc -l'

This prints the directory followed by the number of files in the directory.

---

