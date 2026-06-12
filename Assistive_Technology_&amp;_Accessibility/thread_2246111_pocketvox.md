---
title: "pocketvox"
date: 2014-09-28
forum: Assistive Technology &amp; Accessibility
---

### Post by benoitfra on 2014-09-28
Hello everybody

I'm the main google2ubuntu's developer. And because Google decided to make people using their web speech recognition api with a key that they have to request to Google, I decided to create a library to control my linux desktop using [pocketsphinx]("http://cmusphinx.sourceforge.net/").

This library should make everybody able to rapidly create and deploy a voice controlled application. So I've developed [Pocketvox]("https://github.com/benoitfragit/pocketVox") that you can also find on[ Google+]("https://plus.google.com/communities/101692885089149446503")

The library has been written in C in order to be very efficient. It is developed using a lot of library of the GNOME project such as GLib, GObject, GStreamer,Gtk3,...It is a continuous recording system.


Pocketvox has been built around some (Gobject) object, the first one is a PocketvoxApplication that lets the user manage its module and other parameters. More particularly once the user start the application an applet is displayed in the panel thanks to a PocketvoxIndicator.

Then the user can add/activate/deactivate PocketvoxModule to an application in order to do some actions.

THe library gives also a way to send notifications to the user (sound/visual) thanks to PocketvoxNotifier.

I've written a very simple example that show how to use the Python interface to rapidly create a voice controlled application:

```
#after installing don't forget to set some variable
#/usr/include/espeak/:/usr/local/lib:
#/usr/local/lib/girepository-1.0/:
#
#Now include the Pocketvox module
from gi.repository import Pocketvox as pv
import os


#create your own module very easily by heriting Pocketvox.Module
class MyModule(pv.Module):
    def __init__(self, id, path, tfidf):
        # call the parent constructor
        pv.Module.__init__(self)
        
        # set the module ID (will be display in the applet)
        # set the dictionnary path
        pv.Module.set_property(self, "id", id)
        pv.Module.set_property(self, "dict", path)
    
    # overwrite the execute method of PocketvoxModule    
    def do_execute(self):
        # manage actions or execute commands
        cmd = pv.Module.get_property(self, "cmd")
        print "Result: ", cmd
        os.system(cmd+" &")


#Create a basic application with the path of your profile
#in the future profile will be use to pass to the application 
#personnal data like google account or facebook if developers need this stuff
#
#For the moment a profile contains your name, the espeak voice to use
#and the path to pocketsphinx required files
Application = pv.Application.new("/home/benoit/Bureau/benoit.profile")


#create your new personnal module
mod = MyModule("MyModule", "MyModule.dic", False)


#add your module
Application.add_module(mod)


#launch
Application.start()

```

As you can see building a module is very easy, you only need to specify an id, a dictionnary path and overwrite the execute methode to do some action on your computer. I think there is nothing easier that this.

A dictionnary is basically a txt file with key/value:

> 
open my documents=xdg-open $HOME/Documents
open my musics=xdg-open $HOME/Musics


Each module should be associated to such a dictionnary.

To create a PocketvoxAppliction you should have a profile file that let the user gives some parameters.

I've already posted [a video on youtube]("https://www.youtube.com/watch?v=vDs44L5E1Oo&list=UU3yHmXNVZ1fVzccitCLCvtw") where I show (in french) that we can rapidly control our desktop using pocketvox.

I'm looking for C developers to improve the project. 

If you are interested in my project you can contact me

---

