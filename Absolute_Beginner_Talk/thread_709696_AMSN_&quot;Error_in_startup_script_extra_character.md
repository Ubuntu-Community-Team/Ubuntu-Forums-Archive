---
title: "AMSN &quot;Error in startup script: extra characters after close-brace&quot;"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by cudeso on 2008-02-27
After an upgrade I'm unable to start AMSN. I've tried removing (purge) it and reinstalling. No luck. I've tried both via "apt-get install" and the package provided on the amsn-homepage. No luck. I'm always getting this error:

> 
Error in startup script: extra characters after close-brace
    while executing
"set command [list  $self  {expand}$Snit_optionInfo(configure-$option)  $option]
            "
    invoked from within
"if {$Snit_optionInfo(configure-$option) eq ""} {
                set command [list set ${selfns}::options($option)]
            } else {
             ..."
    (procedure "snit::RT.CacheConfigureCommand" line 32)
    invoked from within
"snit::RT.CacheConfigureCommand  $type $selfns $win $self $option"
    (procedure "::snit::RT.method.configurelist" line 7)
    invoked from within
"::snit::RT.method.configurelist $type $selfns $win $self $args"
    (procedure "::snit::RT.method.configure" line 4)
    invoked from within
"$self configure -width $arrow1width"
    (procedure "::pixmapscrollbar::Snit_constructor" line 52)
    invoked from within
"::pixmapscrollbar::Snit_constructor ::pixmapscrollbar ::pixmapscrollbar::Snit_inst1 .plugins_log.ys .plugins_log.ys -command {.plugins_log.info yview}"
    ("eval" body line 1)
    invoked from within
"eval [linsert $arglist 0  ${type}::Snit_constructor $type $selfns $instance $instance]"
    (procedure "RT.ConstructInstance" line 9)
    invoked from within
"RT.ConstructInstance $type $selfns $name $args"
    (procedure "::snit::RT.widget.typemethod.create" line 54)
    invoked from within
"scrollbar $window.ys -command "$window.info yview""
    (procedure "::pluginslog::draw" line 12)
    invoked from within
"::pluginslog::draw"
    invoked from within
"if { $initialize_amsn == 1 } {
     ::pluginslog::draw
}"
    (file "pluginslog.tcl" line 210)
    invoked from within
"source pluginslog.tcl"
    ("uplevel" body line 27)
    invoked from within
"uplevel \#0 {

        # amsncore.tcl is already loaded but we'll re-source it here in case we manually do reload_files
        source amsncore.tcl
        source audio.tc..."
    (procedure "reload_files" line 2)
    invoked from within
"reload_files"
    (file "/usr/bin/amsn" line 257)



---

### Post by Claus7 on 2008-03-01
Hello,

go to the amsn folder and remove the snit folder that you will find. After that do once again the installation.

Regards!

---

### Post by cudeso on 2008-03-01
I've resolved this by installing the tk8.4 and tk8.4-dev packages. 
After re-installing amsn everything seemed to work. I thought that having the tk8.5 and tk8.5-dev packages whould be sufficient but for one bizarre reason, this is not the case.

---

