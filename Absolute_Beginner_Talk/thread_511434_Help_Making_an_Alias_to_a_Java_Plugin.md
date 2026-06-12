---
title: "Help Making an Alias to a Java Plugin"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by e123 on 2007-07-27
Hi There,

I am running Ubuntu 7.04 on an IBM Thinkpad T41. I need to make an
alias for the Java plugin UnwarpJ. This may not be the best forum to ask...but you all are always very helpful and I hope someone can help me out.

I follow the instructions here ([http://bigwww.epfl.ch/thevenaz/](http://bigwww.epfl.ch/thevenaz/)
UnwarpJ/) and get errors. The output is below. I'm new to Java and
plugins. How do I change the input to the alias command to get a
proper alias to the UnwarpJ program?

Thanks in advance!
e

mdj@lapmdj:~/downloads/ImageJ/plugins/UnwarpJ$ echo $IJDIR
/home/mdj/downloads/ImageJ
mdj@lapmdj:~/downloads/ImageJ/plugins/UnwarpJ$ alias UnwarpJ 'java -
Xmx512m -Dplugins.dir=$IJDIR/plugins -cp $IJDIR/ImageJ.app/Contents/
Resources/Java/ij.jar:$IJDIR/plugins/UnwarpJ UnwarpJ_'
bash: alias: UnwarpJ: not found
bash: alias: `java -Xmx512m -Dplugins.dir': invalid alias name
mdj@lapmdj:~/downloads/ImageJ/plugins/UnwarpJ$

The directory where the UnwarpJ plugin is stored looks like this:
mdj@lapmdj:~/downloads/ImageJ/plugins/UnwarpJ$ ls
UnwarpJ_.class                unwarpJDialog$9.class
unwarpJClearAll.class         unwarpJDialog.class
unwarpJCredits$1.class        unwarpJFile.class
unwarpJCredits.class          unwarpJFinalAction.class
unwarpJCumulativeQueue.class  unwarpJImageModel.class
unwarpJDialog$10.class        UnwarpJ_.java
unwarpJDialog$11.class        UnwarpJ_.java.backup
unwarpJDialog$1.class         unwarpJMask.class
unwarpJDialog$2.class         unwarpJMathTools.class
unwarpJDialog$3.class         unwarpJMiscTools.class
unwarpJDialog$4.class         unwarpJPointAction.class
unwarpJDialog$5.class         unwarpJPointHandler.class
unwarpJDialog$6.class         unwarpJPointToolbar.class
unwarpJDialog$7.class         unwarpJProgressBar.class
unwarpJDialog$8.class         unwarpJTransformation.class
mdj@lapmdj:~/downloads/ImageJ/plugins/UnwarpJ$

---

### Post by KIAaze on 2007-07-30
Try this:
```

alias UnwarpJ='java -Xmx512m -Dplugins.dir=$IJDIR/ImageJ -cp $IJDIR/ij.jar:$IJDIR/plugins/UnwarpJ UnwarpJ_'
```

The command itself wil probably work, but I'm not sure the program itself will.
The output when running UnwarpJ should be the same as when running:
```
java -Xmx512m -Dplugins.dir=$IJDIR/ImageJ -cp $IJDIR/ij.jar:$IJDIR/plugins/UnwarpJ UnwarpJ_
```

---

