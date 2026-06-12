---
title: "Either Ubuntu has a BUG or something is wrong with this Script?"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-15
Hello Everybody !!!

I want you to test the following Script:

Cause:

Either:
UBUNTU HAS A BUG,
OR:
THE SCRIPT is wrong !!!


_LISTEN TO THE STORY_:

When I run this Script from the Terminal I get: Output A

When I double-click ON the Script & Select "Run in Terminal" I get: Output B

_Question_:
HOW IS THIS POSSIBLE? 


_Do the following_:

1. Create a Folder on your Desktop.

2. Put a couple of ".deb" files inside.

3. Copy the "Script" Provided here inside THAT folder.

4. Run the Script from EITHER the Terminal OR by double-clicking on it.

VOILA !!!!

You are going to get Different results, depending on how you Decide to RUN it.....


Script (copy&paste and give it any name you wish):


#!/bin/bash     

ROOT_UID=0	# Only users with "$UID 0" have root privileges.
E_NOTROOT=67	# Non&#8722;root exit error.


# The following is a Function that is going to be called later.
# Functions MUST ALWAYS be declared first.
# ONLY afterwards, you can use them.
Program()
{
	# We are assuming that when you start this program, you ARE inside the Folder
	# you want to work in.

	ls >> $PWD/files.txt
	# To store all the user names in the root folder in a filename "files.txt"
	# ": > files.txt", empties all the contents of the specific file.

	filename=files.txt
	# We assign the variable "filename" the file "files.txt".
	# We are going to need this later on...

	chmod +x $filename
	# This activates all Execute permissions to the file "users.txt".

	echo -e -n "\a" # Makes a "Beep" noise.


	declare -i i=1

	declare -a allfiles[]
	# We declare an array (= "-a"), which will hold ALL our User names. 


	echo -e "--------------------------------------------------------------------------"

	echo -e "The Files inside this Folder are:\\n"
	# The "-n" = do NOT change line.

	while read one_line_each_time
	# The "one_line_each_time" is a variable name.
	# Every Time we loop, we are going to "read" one line & assing
	# that line to the variable named "one_line_each_time".

	do

		allfiles[i]=$one_line_each_time
		# Every line we read is a File name.
		# And Every File name is saved in diff section of the array.
		# File 1 = allfiles[1],
		# File 2 = allfiles[2],
		# ...etc...

		if [ $one_line_each_time != "$0" ] && [ $one_line_each_time != "$0~" ] \
		&& [ $one_line_each_time != "$filename" ]; then
		# The "$0" & "$0~" is the name of this file - e.g. "create.sh" & "create.sh~"

		echo -e -n "\033[34m"
		# The "-n" = do NOT change line.

		echo $one_line_each_time

		>> $PWD/$one_line_each_time.txt
		
		echo -e -n "\033[0m"
		# The "-n" = do NOT change line.

		# echo story ${allfiles[i]}
		#Use this if you want to see the User names contained in the file. 

		fi

		let i=i+1 	

	done <files.txt

	echo -e "--------------------------------------------------------------------------"


	rm files.txt
	# After we get finished, we delete the file named "files.txt"

	chmod 777 *
	# This activates all Execute permissions to ALL the files inside the Directory.

}

clear
# You would first probably want to clear your "Terminal" window.


Program

exit 0




Question:
How can I make the Script RUN the SAME way using BOTH methods?

Thanks.

---

### Post by sisooktom on 2006-03-15
I don't have an Ubuntu machine handy but if you would explain exactly you are trying to accomplish with this script, we could probably help you better.  Also, no offense meant but your overuse of comments and whitespace, combined with your lack of indenting, really make the script hard to read.

Edit:  I'd bet the reason you're getting different output is because you're not printing the filename if it matches $0, presumably to avoid listing the script itself.  But when you run the script via double click, it probably gets invoked with something like "sh test.sh".  At any rate, I have a hard time believing that this script does whatever it is that you want. . .

---

### Post by dvarsam on 2006-03-15
Well:

1. I want to be able to go inside a Folder containing  some ".deb" files...
2. Then copy temporarily a script inside there...
3. The Script copy ALL the File names of the ".deb" files & paste them into the Filenames of the ".txt" files created inside that folder. Those new ".txt" files will have NO content. They will just have the SAME Filename of the ".deb" files inside that folder...
4. Remove the Script from the Folder...
5. Remove the ".deb" files in some OTHER location (Personal Repo), but keep a list of the exact filenames (or dependencies) a program needs (in case I want to install on an individual basis).

I hope you got this...

---

### Post by sisooktom on 2006-03-15
Like this?

#!/bin/bash

for i in $(ls *.deb);do
   [INDENT]touch ${i}.txt[/INDENT] 
done

rm -i /path/to/deb/files/*.deb

---

### Post by dvarsam on 2006-03-15
Thanks for your reply !

What you suggested did not do anything !!!

(I changed the "/path/to/deb/files" to "$PWD") & got nothing!


For every ".deb" file listed in a folder... (e.g. apache2_2.0.54-5ubuntu4_i386.deb)

Create an equivalent Text file with Same name (e.g. apache2_2.0.54-5ubuntu4_i386_deb)

Notice the ".deb" changed  to "_deb".

Then I will do whatever I want to the ".debs"...

That is all...

Thanks

---

### Post by sisooktom on 2006-03-15
Can you post my modified script?  Because I can promise you it works here ;)

---

### Post by dvarsam on 2006-03-15
#!/bin/bash

for i in $(ls *.deb);do

    touch ${i}.txt

done

rm -i $PWD/*.deb

---

### Post by shawnhcorey on 2006-03-15
Hi,


When you start a script in a terminal, it runs in the current working directory. When you start it from the desktop, it runs in your home directory. Place this at the beginning of you script:

cd folder_with_debs

The environment variable $PWD is created and maintained by bash, which may not be running when you start from the desktop. Use `pwd` instead (see 'man pwd').

Example:
my_pwd=`pwd`


sc

---

### Post by dvarsam on 2006-03-15
For some strange reason, now ALL works fine !!!

Even "sisooktom's" method works now...

I do NOT know why, but suddenly BOTH ways work fine (& the same way)!

I did not touch anything, it just auto-fixed itself....

Thanks though, for all your help !!!

---

