---
title: "[req] some windows commands to linux"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-07-16
im doin a heavy .sh file for linux to run a game, here r some windows commands i need converted to linux so imay use them

i know echo is same but heres the ones i need:

```

TITLE
@ECHO OFF
CLS
GOTO

**heres asome code i got for my .bat:**
	SET option=
	ECHO.
	ECHO ==============================
	SET /p option=Your Choice? 
	if %option%==1 goto runclient
	if %option%==2 goto updateclient
	if %option%==3 goto createaccount
	if %option%==4 goto info
	if %option%==5 exit
**i need that converted ^^^^^^^^^^^^**

PAUSE

DEL = rm i think

```

and thats it ty for help

---

### Post by [S|G] on 2006-07-16
> **Goat Spirit said:**
> im doin a heavy .sh file for linux to run a game, here r some windows commands i need converted to linux so imay use them

i know echo is same but heres the ones i need:

```

TITLE
@ECHO OFF
CLS
GOTO

**heres asome code i got for my .bat:**
	SET option=
	ECHO.
	ECHO ==============================
	SET /p option=Your Choice? 
	if %option%==1 goto runclient
	if %option%==2 goto updateclient
	if %option%==3 goto createaccount
	if %option%==4 goto info
	if %option%==5 exit
**i need that converted ^^^^^^^^^^^^**

PAUSE

DEL = rm i think

```

and thats it ty for help
You don't need to set Echo off
Echo = echo (no uppercase)
cls = clear

You might want to create functions when you want to "go to". You can do something like this:
```

Info()
{
 echo 'I am a simple example of function. You can place any commands you want here'
}

```
When you want to display Info, simply use Info as a command. Your code would look like something like this:
```

#!/bin/bash
#This is a comment. You can add comments by using the # character. 
#Everything after it will be treated as a comment and not code.

option=" "          #This will blank the option variable.

Info()              #This is the Info function you'll be calling later.
{
 echo 'I am a simple example of function. You can place any commands you want here'
}


echo " "
echo "=============================="
echo "What is your choice?"
read option          #This will accept input and store it on option
case $option in     #Since you're going to have multiple choices, case is better than a lot of "if"s. 
                           #Case will evalute the value and act accordingly.
  "1")                 #Action if option had a value of 1
    Runclient;;
  "2")                 #Action if option had a value of 2
    Updateclient;;
  "3")                 #Action if option had a value of 3
    CreateAccount;;
  "4")                 #Action if option had a value of 4
    Info;;
  "5")                 #Action if option had a value of 5
    Exit;;
esac                 #End of case. Note that its case written backwards

```
Note that option 4 would work since you defined Info. You still need to define the other options.

You can use the "if" clause this way:
```

if [ $variable = "value" ]             #begin of if clause.
then
  echo 'This is a message that would appear if variable had value of value'
elif [ $variable = "value2" ]
  echo 'This would appear if variable had value of value2 instead'
else
  echo 'This would appear if variable had any other value'
fi                                     #end of if clause

```

---

### Post by Ben Sprinkle on 2006-07-16
im understanding some of this so anyway insted of

::info

its 

info()
??

---

### Post by [S|G] on 2006-07-16
I just edited the code a bit to add how to use the if clause.
Info() is a function that you can call any time in the program. It would be very similar to ::info in a batch file.

---

### Post by Ben Sprinkle on 2006-07-16
ok well anyway heres my fuull .bat file im workin on fully workin in windows:

```

TITLE Endar
@ECHO OFF
CD files

:info
	CLS
	ECHO ==============================
	ECHO Endar
	ECHO ===
	ECHO Made by Goat Spirit
	ECHO ===
	ECHO goat_spirit@hotmail.com
	ECHO ==============================
	PAUSE
	CLS
	GOTO menu

:menu
	CLS
	ECHO ==============================
	ECHO Type 1 to start the Endar Client.
	ECHO Type 2 to start the Endar Updater.
	ECHO Type 3 to start the Website Stealer.
	ECHO Type 4 to view info.
	ECHO Type 5 to exit.
	SET option=
	ECHO.
	ECHO ==============================
	SET /p option=Your Choice? 
	if %option%==1 goto runclient
	if %option%==2 goto updateclient
	if %option%==3 goto createaccount
	if %option%==4 goto info
	if %option%==5 exit

:runclient
	CLS
	ECHO ==============================
	ECHO When you are ready to start
	ECHO Endar, press enter.
	ECHO ==============================
	PAUSE
	CLS
	GOTO startclient

:startclient
	CLS
	ECHO ==============================
	JAVA client
	ECHO Press ENTER to go back to the menu.
	ECHO ==============================
	PAUSE
	CLS
	GOTO menu

:updateclient
	CLS
	ECHO ==============================
	CD ../
	ECHO WGET is updating Endar
	ECHO ===
	WGET http://goat-spirit.com/Files/Endar.zip
	ECHO ===
	ECHO Press enter to extract archive.
	ECHO ==============================
	PAUSE
	CLS
	GOTO extract

:extract
	CLS
	ECHO ==============================
	ECHO Extracting new Endar archive...
	ECHO ===
	JAVA Unzipper Endar.zip
	ECHO ===
	ECHO All done...press enter to go to menu.
	ECHO ==============================
	PAUSE
	DEL Endar.zip
	CD files
	CLS
	GOTO menu

:createaccount
	CLS
	ECHO DOWNLOADS WILL BE IN FILES/SITESTEALER/DOWNLOADS XD
	JAVA -Xmx500m Grab
	PAUSE
	CLS
	GOTO menu

```

i still gotta get wget XD

---

### Post by [S|G] on 2006-07-16
You would just need to create the function Menu():
```

Menu(){
echo " "
echo "=============================="
echo "What is your choice?"
read option          #This will accept input and store it on option
case $option in     #Since you're going to have multiple choices, case is better than a lot of "if"s. 
                           #Case will evalute the value and act accordingly.
  "1")                 #Action if option had a value of 1
    Runclient;;
  "2")                 #Action if option had a value of 2
    Updateclient;;
  "3")                 #Action if option had a value of 3
    CreateAccount;;
  "4")                 #Action if option had a value of 4
    Info;;
  "5")                 #Action if option had a value of 5
    Exit;;
esac                 #End of case. Note that its case written backwards
}

```
Then you can call it anytime in the program. After you set the functions, just call the menu and then it'll start the program loop. 

You can use linux's wget and unzip commands to get the files and unzip them. You can always check their manpages (man wget for example) to see how to use them.

---

### Post by Ben Sprinkle on 2006-07-16
ok i think i got it thanks alot uv been a help

---

### Post by Ben Sprinkle on 2006-07-16
oh one more thing whats pause in linux terms?

---

### Post by [S|G] on 2006-07-16
I'm not sure whether there is a "pause" command. Usually when I need to pause until the user press enter, I simply do this:
```

read tmp

```
This would actually dump the input into a variable called "tmp" (which I use for temporary storage or just for pausing anyway).

If you plan to display a large ammount of text into the screen, you can do something like:
```

echo 'this would be a big, mean, large ammount of text'|more

```
That would pause the program until the user pressed enter or space every time the text filled the screen.

EDIT: You might want to read this section of Rute: [http://rute.2038bug.com/node10.html.gz](http://rute.2038bug.com/node10.html.gz)

---

