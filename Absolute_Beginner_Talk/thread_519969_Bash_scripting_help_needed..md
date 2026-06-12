---
title: "Bash scripting help needed."
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by jonyboy1000 on 2007-08-07
Hi all I have this script and one of the commands is

```
su - jonathan /home/guest/script
```

This allows the user guest to login to my account on the command line and execute the command "/home/guest/script". The user "guest" has to type in my password.

I was wondering how to use an if/else statement to say whether or not the user succeeded.

I want it to say incorrect password

or

Permission granted

but don't know how to capture the user input whilst they type in the password when "su - jonathan" asks for it.

Thanks

---

### Post by milosz.galazka on 2007-08-07
Hello,

Can't you create group based policy to run this script?

But if someone needs your privileges... I will put script here in next 10 minutes :)

---

### Post by milosz.galazka on 2007-08-07
```
#!/bin/sh

# user and command for su
user="user"
command="/bin/echo"

# debug 0/1
debug=0;

# variable holding exit code after su execution
exit_code=0;

# our function
runme(){
 # We need to show this to user
 echo -n "Password: "
 result=`su - $user -c $command 2>&1`
 exit_code=$?

 echo

 # debug
 if [ "$debug" = "1" ]; then
  echo "code: " $exit_code;
  echo "result: " $result;
 fi

 # user output
 # you can use logger to log everything
 # or simply use echo "something" > /home/myser/mysmalllog.file
 if [ "$exit_code" =  "0" ]; then
  echo "ok";
 else
  echo "something gone wrong ($exit_code)";
 fi

}

# so lets start it
runme

```

If you want to use that or similar script remember about one thing:
If your script fails then you will see something like *something gone wrong (127)*

---

