---
title: "Execute Command in a Background Process"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by viper2843 on 2007-06-30
I have a program that takes over the shell very similar to how MySQL takes over the shell until you exit it.  Since it is a server application I don't need to access it very often and since I start the application when I start the computer, the process starts in the background.  What I want to do is write a bash script to execute a few basic commands that I would normally execute if the program was launched normally.  Is there a way to get control of a process, execute a command, and get the results back to process and display?  I can very easily get the PID of the application if that is needed.  Thank you in advance.

---

### Post by energiya on 2007-07-02
> **viper2843 said:**
> What I want to do is write a bash script to execute a few basic commands that I would normally execute if the program was launched normally.  Is there a way to get control of a process, execute a command, and get the results back to process and display?  I can very easily get the PID of the application if that is needed.  Thank you in advance.

This script will run the commands only if process_name is running.
> 
#!/bin/sh
logfile=$HOME"/.testrunlog"
timestamp=`date +%T" "%D`
uselog=1

if [ -n "$1" ]; then
  test=`ps -C $1 | grep $1`
  if [ "$test" == "" ]; then
    if [ -n "$2" ]; then
      $2
    else
      $1
    fi
    if [ $uselog -eq 1 ]; then
      echo "$timestamp: $1 not found. Executing $2" >> $logfile
    fi
  else
    if [ $uselog -eq 1 ]; then
      echo "$timestamp: $1 found. Not executing $2" >> $logfile
    fi
  fi
else
  echo "Usage: $0 process_name [command]"
fi

You can copy this in a file called "testrun" (or whatever) and "chmod +x NAME". If you like it you can copy the script to /usr/bin or /usr/local/bin for easy acces.

_Example of usage:_
testrun irexec "irexec -d ~/.lircrc"
        will test if irexec is started and execute "irexec -d ~/.lircrc" only if it isn't.

testrun conky "echo \"Error! Conky wasn't running!\" && echo \"Trying to start\" && conky && htop"
        will test if conky is started and execute "..." if not.

The script will also log the activity (if you put uselog=1) to a file named .testrunlog in your home directory (you can change the path and filename). Change to uselog=0 if you don't want that.

You can find out what process_name is by using htop, top or any other simmilar app (taskmanager like).

Hope this helps. Post any problems/requests here.

---

