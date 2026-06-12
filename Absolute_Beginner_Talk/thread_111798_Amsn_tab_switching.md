---
title: "Amsn tab switching"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by rizzyc on 2006-01-03
i found this patch on sourceforge but i dont know how to apply it can some one help me?
```

Modifications to enable cycling through tabs using <crtl>+<tab> and close the
current tab by pressing <crtl>+<F4>.

Add these lines to ::ChatWindow::CreateContainer (which is in chatwindow.tcl, search for "bindings")
		
		bind $w <Control-KeyRelease-Tab> "::ChatWindow::GoToNextTab $w"
		bind $w <Control-F4> "::ChatWindow::CloseTab \[set ::ChatWindow::win2tab(\[::ChatWindow::GetCurrentWindow $w\])\]"		

and add the following procedure:
	
	#///////////////////////////////////////////////////////////////////////////////
	# ::ChatWindow::GoToNextTab ( container )
	# Used to switch to the next tab in a container. Called by the binding for the
	# <alt>+<tab> key combination. The list of windows in the container is used to
	# determine the next tab. ::ChatWindow::SwitchToTab is used for switching.
	# Arguments:
	# - container => The container window in which the current tab is located.
	proc GoToNextTab { container } {
	    set currentWin [::ChatWindow::getCurrentTab $container]
	    set windows [set ::ChatWindow::containerwindows($container)]
	    set tabPos [lsearch $windows $currentWin]
	    
	    # If the current tab is the last go the the first, else go to the next.
	    if { $tabPos == [expr [llength $windows] - 1] } {
		set nextTab 0
	    } else {
		set nextTab [expr $tabPos + 1]
	    }
	    
	    SwitchToTab $container [lindex $windows $nextTab]
	}
	#///////////////////////////////////////////////////////////////////////////////

```

---

### Post by rizzyc on 2006-01-04
bump

---

