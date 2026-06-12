---
title: "some1 explain this to me"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-07-16
wdf im makin a .sh file ok/?

i did a guide by S|G this was what he told me tp put i think

```

read option
case $option in		#start of choices
if [$VAR = "1"]             #begin of if clause.
then
  echo 'This is a message that would appear if variable had value of value'
elif [$VAR = "2"]
  echo 'This would appear if variable had value of value2 instead'
else
  echo 'This would appear if variable had any other value'
fi                                     #end of if clause
esac                 #End of case. Note that its case written backwards

```

this is the error i got wdf

```

==============================
Type 1 to start Endar.
Type 2 to start the Endar Updater.
Type 3 to start the Website Stealer.
Type 4 to view info.
Type 5 to exit
==============================
Your Choice?

/home/endar/Desktop/Endar - Linux Version/Endar Main Startup.sh: line 28: syntax error near unexpected token `[$VAR'
/home/endar/Desktop/Endar - Linux Version/Endar Main Startup.sh: line 28: `if [$VAR = "1"]             #begin of if clause.'


```

help

---

### Post by Ragazzo on 2006-07-16
[http://www.tldp.org/LDP/abs/html/testbranch.html#EX30]("http://www.tldp.org/LDP/abs/html/testbranch.html#EX30")

```

read option
case $option in
1 )  echo 'This is a message that would appear if variable had value of value' ;;
2 )  echo 'This would appear if variable had value of value2 instead' ;;
* )  echo 'This would appear if variable had any other value' ;;
esac

```

---

### Post by Ben Sprinkle on 2006-07-16
omfg yes tytytytytyty!!!!!!!!!!!!!!!1

---

