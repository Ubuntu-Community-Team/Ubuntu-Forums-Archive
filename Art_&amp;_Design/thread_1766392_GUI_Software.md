---
title: "GUI Software?"
date: 2011-05-24
forum: Art &amp; Design
---

### Post by ankeetg on 2011-05-24
Hey!

I need a software that will help me make a GUI.

Obviously, I'm looking for something that's easy to use and quick to learn.

I'm looking to have the following capabilities from my GUI: display contents from a MySQL table, execute some terminal code when a button is pressed.

My program has been made using C and the MySQL table has also been created.

I've already looked at gtk+/glade, and have tried going through various tutorials.
The one by Micah Carrick seems outdated, and I went through one which was quite useful by Tadej Borovsk. However, I'm still finding it hard to grasp the callback functionality as I'm not familiar with any of these toolkits. Also, it's really hard to find tutorials in specific.

I'm looking to whip a functional GUI in about 3-4 days time. Any suggestions?

I'm comfortable with C and C++.

I'll appreciate any help!

Thanks!

---

### Post by Petrolea on 2011-05-24
For ideas and code samples I always looked at GTK+ forums, it is very useful. 

If you want a functional GUI in 3-4 days, you can use just code, it really isn't that hard.

You use callbacks when you want a specific function to be called when some event happens (click for example). You can tell which functions to call on which event in Glade also, then just write the function in your source file (must be the same name ofcourse).

---

### Post by BrandonC19 on 2011-05-24
The Qt Designer has served me well for the one time I made a gui for a C++ program.

---

### Post by ankeetg on 2011-05-24
Thanks for the prompt reply!

I mean, I understand what the callbacks are for. But I'm just wondering if the GTK toolkit will be to expansive for me to learn.

Basically, I'm wondering if somethig like this is possible.

In Glade, I have a button, and I've set an on_click signal handler to it. 
After creating the main.c file and the callbacks.c file, is it possible for me to just code the function something like
functionname (GtkBuilder *builder, etc etc)
{
/*My terminal codeof sorts*/
}

Is something like that possible or do I've to know specific function names or something of that sort?
Thanks again.

@Brandon
I'm just downloading Qt now actually.. How complicated are the callbacks to code? Do you have to be very familiar with the qt toolkit? Thanks for the response!

---

### Post by Petrolea on 2011-05-24
> **ankeetg said:**
> Thanks for the prompt reply!

I mean, I understand what the callbacks are for. But I'm just wondering if the GTK toolkit will be to expansive for me to learn.

Basically, I'm wondering if somethig like this is possible.

In Glade, I have a button, and I've set an on_click signal handler to it. 
After creating the main.c file and the callbacks.c file, is it possible for me to just code the function something like
functionname (GtkBuilder *builder, etc etc)
{
/*My terminal codeof sorts*/
}

Is something like that possible or do I've to know specific function names or something of that sort?
Thanks again.

@Brandon
I'm just downloading Qt now actually.. How complicated are the callbacks to code? Do you have to be very familiar with the qt toolkit? Thanks for the response!

Function that you want to call can have any name as long as it is the same name as the program calls when event happens. Simply connect the event to this function and it should work. 

Example:

Function:
```

void change_value (lalala)
{
	/* Do your work */
}

```

Signal connect:
```

g_signal_connect(button, "clicked", G_CALLBACK(change_value), object);

```

---

### Post by ankeetg on 2011-05-24
Thanks Petrolea!

I'll run a few sample tests and get back to you!! thanks again!

---

### Post by Petrolea on 2011-05-24
> **ankeetg said:**
> Thanks Petrolea!

I'll run a few sample tests and get back to you!! thanks again!

No problem, I'm here to help :) If you have any more questions, make sure to ask.

---

