---
title: "shell script help"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2006-11-27
I am trying to make a student task manager. This isn't important but I am hooked on trying to program my computer. I'm a beginner so have come across a few problems and need some assistance, so if anyone can help I would be very grateful.

Does anyoneknow how to do the following:

1. I have a file called data.txt, in the file data.txt is a word. This word can be either "sort" or "cat", however I need this word to be read into a shell script. Now, what I want to do is, read from this file and use the word to output the details of another file called "mywords"

For example, myscript.sh:

File='data.txt'
$File mywords

If the word in data.txt was "sort" then it would sort mywords file according to the sort criteria. If the word was "cat" then it would just normally output the contents of the mywords file.

2. I have a file called tasks that need the list to be sorted out according to each row individually, priority, date, description:

Priority        Date       Description
-----------------------------------------------------------
1 High (P)	27/11/06   This is a high priority task
1 High (P)	27/11/06   this is a high preiority task 2
2 Medium (P)	27/11/06   This is a medium level task
3 Low (P)	27/11/06   this is a low level task
2 Medium (P)	27/11/06   This is a medium level task
2 Medium (P)	27/11/06   This is a medium level task
1 High (P)	27/11/06   This is a high leveltask
3 Low (P)	27/11/06   this is a low level task

I ran through the sort command but can't work it out at all. Can anyone help with this?

3. Taking into consideration the same file in number 2, does anyone know how I can read the file for the dates, compare it todays date and if it matches, output that line only?

---

### Post by Bagboy23 on 2006-11-27
This is the todo manager I am trying to make. It's just a simple one for the terminal, think it will look good with XGL/Beryl. It's quite messy:

```
#Date created: 26/11/06
##Begin Code

#Variables
FILE=datafile

clear

echo ""
echo "                        T O D O  M A N A G E R"
echo "Today's tasks are:"
echo "--------------------------------------------------------------------------"
echo "Pri		Due Date     Description"			          	  
echo "--------------------------------------------------------------------------"
cat $FILE | grep -A 1 "$(date +%x)"
echo "\n\n\n"
echo "Other Tasks:"
echo "--------------------------------------------------------------------------"
echo "Pri		Due Date     Description"			          	  
echo "--------------------------------------------------------------------------"
cat datafile
echo "\n"
echo -n "# "
read command
case "$command" in
	v)
		echo "Today's tasks are:"
		cat datafile
		;;
	c)
              echo "" >> datafile

		#Insert Priority		
		echo "Enter Priority; high/medium/low"
		read priority
		
		case "$priority" in
			
			high)
			    echo -n "1 High (P)\t" >> datafile
			    ;;	

		      medium)
			    echo -n "2 Medium (P)\t" >> datafile
			    ;;

		         low)
			    echo -n "3 Low (P)\t" >> datafile
			    ;;

			   *)
			     clear			    
			     echo "Bad command. Returing to main screen."
		       	     sleep 1
			     sh ./todo2.sh
			    ;;

		esac
		
		#Insert Date
		
		echo "Enter The completion month (MM):"
		read dmonth

		echo "Enter the day (DD):"
		read dday

		echo "Enter the Year (YYYY):"
		read dyear

		echo -n "$dmonth/" >> datafile
		echo -n "$dday/" >> datafile
		echo -n "$dyear" >> datafile
		echo -n "   " >> datafile	
                
		#Insert Description
		echo "Enter Description"
		read desc
		echo -n "$desc" >> datafile
		#echo -n "      Date Added: $(date +%x)" >> datafile
        	sh ./todo2.sh

		;;
	h)
			echo "This is a test"
			;;
		
	*)
	       clear			    
	       echo "Bad command. Returing to main screen."
	       sleep 1
	       sh ./todo2.sh
		;;
esac

exit 0

```

---

### Post by po0f on 2006-11-28
Bagboy23,

If it's not already there, you should put a hash-bang line as the first line:
```
[FONT="Courier New"]#!/bin/bash[/FONT]
```
or whatever your preferred script interpreter is.

Instead of calling echo five thousand times at the beginning of your script, you can just call it once like so:
```
[FONT="Courier New"]echo -e "\n\
                        T O D O  M A N A G E R\n\
Today's tasks are:\n\
--------------------------------------------------------------------------\n\
Pri		Due Date     Description\n\
--------------------------------------------------------------------------\n\"[/FONT]
```
And so on and so forth.

When you're read'ing the priority in, you can have several options for one case, ie:
```
[FONT="Courier New"]case "$priority" in
    high | h)
        # do stuff
        ;;
    medium | m)
        # do stuff
        ;;
    low | l)
        # do stuff
        ;;
esac[/FONT]
```
It might make it a little easier to use.

If there's anything else that's bugging you, post back.  You might find [this link](http://tldp.org/LDP/abs/html/abs-guide.html) indispensable while hacking your scripts together, I know I do.  ;)  It's conveniently in the [repos](http://packages.ubuntu.com/edgy/doc/abs-guide) if you want to have it available for off-line browsing as well.

[EDIT]

[Colors](http://www.faqs.org/docs/abs/HTML/colorizing.html) are pretty as well.  :)

---

### Post by David_T on 2006-11-28
If you want to pull out just the lines that match the current date, and you always write the date in that format--day/month/year--you can do it like this:

grep `date +%e/%m/%y` yourtodolistfile

---

### Post by Bagboy23 on 2006-11-28
Lol@my abilities, but thanks alot for the help. You guys provided some really good help tomake my thing look cooler.

Does anyone have an answer to my first post?

---

### Post by po0f on 2006-11-28
Bagboy23,

Instead of *data.txt*, I would suggest renaming this file *command.txt* (it's a little more descriptive) and renaming the variable *command* instead of *File*.
```
[FONT="Courier New"]command=`cat command.txt|sed -e 's/[[:space:]]//g'`[/FONT]
```
The sed snippet in the above code just strips the space around whatever command is in there.  Make sure it's just one word, because it strips all the space so something like *cat sort* gets turned into *catsort*.

I can't give any advice on sort as I haven't used it much myself.  Sorry.

---

