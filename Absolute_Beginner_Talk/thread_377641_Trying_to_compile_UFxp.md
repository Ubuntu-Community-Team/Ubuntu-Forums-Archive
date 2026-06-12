---
title: "Trying to compile UFxp"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by gardara on 2007-03-06
I am trying to compile UFxp (gui for FXP.One)

I have followed all steps here:

[http://www.lundman.net/wiki/index.php/UFxp:build](http://www.lundman.net/wiki/index.php/UFxp:build)

But when I try to compile UFxp with TheIDE Gui I get these errors:

```

----- UFxp ( GUI MT MAIN GCC32 DEBUG SHARED DEBUG_FULL BLITZ LINUX ) (11 / 11)
BLITZ: Misc.cpp OptionMgr.cpp SiteMgr.cpp Trans.cpp main.cpp QueueList.cpp EditSite.cpp
In file included from /home/gardar/upp/out/UFxp/GCC32.Debug_full.Gui.Main.Mt.Shared/$blitz.cpp:32:
/home/gardar/upp/MyApps/UFxp/QueueList.cpp:362:2: warning: no newline at end of file
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp: In member function &#145;void OptionMgr::SaveConfig()&#146;:
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:89: error: &#145;Upp&#146; has not been declared
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:90: error: &#145;Upp&#146; has not been declared
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:91: error: &#145;Upp&#146; has not been declared
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:92: error: &#145;Upp&#146; has not been declared
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:93: error: &#145;Upp&#146; has not been declared
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:94: error: &#145;Upp&#146; has not been declared
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:95: error: &#145;Upp&#146; has not been declared
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:96: error: &#145;Upp&#146; has not been declared
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp: In member function &#145;void OptionMgr::LoadConfig()&#146;:
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:125: error: &#145;GuessCWDPath&#146; was not declared in this scope
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp: At global scope:
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:199: error: no &#145;void OptionMgr::GuessCWDPath()&#146; member function declared in class &#145;OptionMgr&#146;
	
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp: In member function &#145;void OptionMgr::GuessCWDPath()&#146;:
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:205: error: &#145;GuessCheckPath&#146; was not declared in this scope
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:226: error: &#145;GuessCheckPath&#146; was not declared in this scope
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:232: error: &#145;GuessCheckPath&#146; was not declared in this scope
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:234: error: &#145;GuessCheckPath&#146; was not declared in this scope
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:236: error: &#145;GuessCheckPath&#146; was not declared in this scope
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:237: error: &#145;GuessCheckPath&#146; was not declared in this scope
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:239: error: &#145;GuessCheckPath&#146; was not declared in this scope
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp: At global scope:
/home/gardar/upp/MyApps/UFxp/OptionMgr.cpp:250: error: no &#145;int OptionMgr::GuessCheckPath(String)&#146; member function declared in class &#145;Optio
	nMgr&#146;
/home/gardar/upp/MyApps/UFxp/main.cpp: In member function &#145;void UFxp::do_EngDlg()&#146;:
/home/gardar/upp/MyApps/UFxp/main.cpp:439: error: &#145;UFXP_VERSION&#146; was not declared in this scope
/home/gardar/upp/MyApps/UFxp/main.cpp:444: error: expected `)' before &#145;UFXP_VERSION&#146;
/home/gardar/upp/MyApps/UFxp/main.cpp: In member function &#145;void UFxp::do_CopyNames(bool)&#146;:
/home/gardar/upp/MyApps/UFxp/main.cpp:1188: error: expected primary-expression before &#145;<<&#146; token
/home/gardar/upp/MyApps/UFxp/main.cpp:1188: error: expected primary-expression before &#145;<<&#146; token
/home/gardar/upp/MyApps/UFxp/main.cpp:1188: error: expected primary-expression before &#145;<<&#146; token
/home/gardar/upp/MyApps/UFxp/main.cpp:1188: error: expected primary-expression before &#145;<&#146; token
/home/gardar/upp/MyApps/UFxp/main.cpp:1188: error: &#145;main&#146; was not declared in this scope
/home/gardar/upp/MyApps/UFxp/main.cpp:1190: error: expected primary-expression before &#145;==&#146; token
/home/gardar/upp/MyApps/UFxp/main.cpp:1190: error: expected primary-expression before &#145;==&#146; token
/home/gardar/upp/MyApps/UFxp/main.cpp:1190: error: expected primary-expression before &#145;=&#146; token
/home/gardar/upp/MyApps/UFxp/main.cpp:1192: error: expected primary-expression before &#145;>>&#146; token
/home/gardar/upp/MyApps/UFxp/main.cpp:1192: error: expected primary-expression before &#145;>>&#146; token
/home/gardar/upp/MyApps/UFxp/main.cpp:1192: error: expected primary-expression before &#145;>>&#146; token
/home/gardar/upp/MyApps/UFxp/main.cpp:1192: error: expected primary-expression before &#145;>&#146; token
/home/gardar/upp/MyApps/UFxp/main.cpp:1193: error: expected `;' before &#145;}&#146; token
UFxp: 7 file(s) built in (0:02.03), 290 msecs / file, duration = 2046 msecs

There were errors. (1:01.34)

```


Can anyone help me out?

---

