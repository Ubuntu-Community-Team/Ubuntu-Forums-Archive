---
title: "Confusion about environment variables"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-04-18
Hi... I hijacked a thread earlier, but have repented of my ways... so here's the question in its own thread:

I want to write some Gnome apps in Mono and Gtk#, so I'm learning like C# and Gtk# and all that dotnet stuff (so I can port the app later to WIndows, if I want. DOne some programming in VB and VBA, so I kinda know the environment. I installed the required packages through Synaptic and was able to create the usual "hello-world" thingie in the MonoDevelop GUI, which compiled just fine in the GUI:
```
Building Project: Tutorial_A Configuration: Debug
Performing main compilation...
Build complete -- 0 errors, 0 warnings
---------------------- Done ----------------------
Build successful.
```
However, to *run* the hello.cs file, I'm meant to do a:
```
mcs hello.cs -pkg:gtk-sharpgdm.conf

```
This generated the following error:
>  Source file `Main.cs' could not be found
Compilation failed: 1 error(s), 0 warnings

...which I attribute to a PATH issue. I've had a look at the /etc/bash.bashrc file - the whole thing looks like a PERL script, which I'm not familiar with at all (there's a number of IF conditional statements towards the bottom - the rest appears to be more appearance, autocompletion and stuff like that) and I don't really want to muck with any of that... anyway, I simply cannot figure out where I would add a path statement.

Or, am I barking up the wrong tree? Is this something I should be doing in some conf file for MonoDevelop?
Thanks to all who reply...

---

### Post by lukew on 2007-04-18
> **Robynsveil said:**
> Hi... I hijacked a thread earlier, but have repented of my ways... so here's the question in its own thread:

I want to write some Gnome apps in Mono and Gtk#, so I'm learning like C# and Gtk# and all that dotnet stuff (so I can port the app later to WIndows, if I want. DOne some programming in VB and VBA, so I kinda know the environment. I installed the required packages through Synaptic and was able to create the usual "hello-world" thingie in the MonoDevelop GUI, which compiled just fine in the GUI:
```
Building Project: Tutorial_A Configuration: Debug
Performing main compilation...
Build complete -- 0 errors, 0 warnings
---------------------- Done ----------------------
Build successful.
```
However, to *run* the hello.cs file, I'm meant to do a:
```
mcs hello.cs -pkg:gtk-sharpgdm.conf

```
This generated the following error:

...which I attribute to a PATH issue. I've had a look at the /etc/bash.bashrc file - the whole thing looks like a PERL script, which I'm not familiar with at all (there's a number of IF conditional statements towards the bottom - the rest appears to be more appearance, autocompletion and stuff like that) and I don't really want to muck with any of that... anyway, I simply cannot figure out where I would add a path statement.

Or, am I barking up the wrong tree? Is this something I should be doing in some conf file for MonoDevelop?
Thanks to all who reply...

Does hello.cs have a main method defined with "puiblic static void" ?

---

### Post by Cypher on 2007-04-18
Post your code, so we can help..

Regards

---

### Post by Robynsveil on 2007-04-19
> **Cypher said:**
> Post your code, so we can help..

Regards

Sure, be happy to. This is the code from hello.cs

```
 // 04-gtk/01-basics
using System;
using Gtk;
class MainClass {
    public static void Main (string[] args)
    {
        Application.Init ();
        Window w = new Window ("Gtk# Basics");
        Button b = new Button ("Hit me");
        w.DeleteEvent += new
        DeleteEventHandler (Window_Delete);
        b.Clicked += new
        EventHandler (Button_Clicked);
        // initialize the GUI
        w.Add (b);
        w.SetDefaultSize (200, 100);
        w.ShowAll ();
        Application.Run ();
    }
    static void Window_Delete (object o,
        DeleteEventArgs args)
    {
        Application.Quit ();
        args.RetVal = true;
    }
    static void Button_Clicked (object o, EventArgs
        args)
    {
        System.Console.WriteLine ("Hello, World!");
    }
}
```

and this is the code from echo.cs:

```
// created on 4/16/2007 at 8:51 AM
using system;

  namespace HelloUtil
  {
  
    public class Echo
    {
      string c_String;
      
      public Echo(string aString)
      {
        c_String = aString;
      }
    }
    
    public void Tell()
    {
      Console.WriteLine(c_String);
    }
  
  }
```

This all complied fine in the MonoDevelop GUI.

---

