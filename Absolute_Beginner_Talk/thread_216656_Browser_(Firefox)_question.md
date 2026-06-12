---
title: "Browser (Firefox) question"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2006-07-15
When I click on the chat button on my DSL providers' website (Verizon), this is a bit of what I get.  Why am I getting this ?  And how do I fix it ?  Thanks.

<html>
<head>


<TITLE>Verizon Central - Login</TITLE>
<META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=UTF-8">
<META HTTP-EQUIV="expires" CONTENT="Mon, 1 May 1995 00:00:00 EST"/>

<script LANGUAGE="JavaScript1.2"><!--

//if( !parent.Content && top.Content )
		//{
 		//top.Content.location = this.location
  //}
function KeyUp(event)
{
    if(navigator.appName == 'Microsoft Internet Explorer')
    {
        currentElement = document.activeElement;
        currentKey = window.event.keyCode;
        if (currentKey == 13 && currentElement.value != "")
        {
            validateUser();

---

### Post by catlett on 2006-07-15
Did you install java? It looks like firefox is printing out the javascript in text instead of the script activating java and running an applet.
I am not a java expert but I thought I would throw it out there.

---

### Post by testube_babies on 2006-07-15
I'm pretty sure that Java and Javascript are two wholly seperate languages, and that one has no effect on the other.  That being said, I have no idea why the browser isn't reading the script correctly.

Firefox has a built-in Javascript console.  It's in the 'Tools' menu.  Maybe if it prints out errors it could help.

---

### Post by wpshooter on 2006-07-16
> **catlett said:**
> Did you install java? It looks like firefox is printing out the javascript in text instead of the script activating java and running an applet.
I am not a java expert but I thought I would throw it out there.

I just install JAVA (or at least I gave it my best shot, using EasyUbuntu) and when I go to the Verizon site and click on the chat link, I **still** get the same thing.

How do I go about checking to make sure that JAVA did in fact properly install ?

Thanks.

---

### Post by wpshooter on 2006-07-16
After much research and checking, I am fairly confident that I have JAVA properly installed.  At least that is what I interpreted one of the commands that I ran at the terminal as saying.

However, when I go back to the original problem of trying to run the Verizon chat session, I still get the same problem as related in my original posting.

Is it possible that whatever skeem of things Verizon is running is just NOT compatible with FIREFOX and UBUNTU ?

When I called them, they said that they did not support Ubuntu/Linux !!!

Thanks.

---

