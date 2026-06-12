---
title: "undefined reference error when compiling gtk apps"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by mycoplasma on 2006-10-15
sorry if this is in the wrong forum; i wasn't sure if i should put it in programming talk or absolute beginner talk



I just started reading the GTK+ tutorial at [http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/) and i am stuck at the very beginning because i cannot compile the first example, a program that creates a window with gtk and does nothing.  Everytime i try to compile it, gcc gives me this output:

> 
/usr/local/lib/libpango-1.0.so: undefined reference to `g_type_register_static_simple'
collect2: ld returned 1 exit status


I'm not sure, but I think the problem might be related to either a missing header file or a linker error because using synaptic to download newer versions of Glib, GTK, and pango have not fixed this problem.  Here is the source code:

> 
#include <gtk/gtk.h>

int main( int   argc,
          char *argv[] )
{
    GtkWidget *window;
    
    gtk_init (&argc, &argv);
    
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_show  (window);
    
    gtk_main ();
    
    return 0;
}


and here is what i type into the command line to invoke gcc:

> 
 gcc base.c -o base `pkg-config --cflags --libs gtk+-2.0`


can someone please help me?

---

