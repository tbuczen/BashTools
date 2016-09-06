# shellScripts
useful aliases and function to improve workflow

#Typos

alias xs='cd'
alias vf='cd'
alias moer='more'
alias moew='more'
alias kk='ll'


#Personal shortcuts

alias printBetween='tr -d "\n\r" < gts.phtml | grep -Po '".*?"' '  #print file content between ""
alias fuck='sudo $(history -p \!\!)'                               #redo previous command but with sudo

#Symfony aliases
alias sf="php app/console"
alias sfdev="php app/console --env=dev"
alias sfprod="php app/console --env=prod"

# Aliases                                
alias install='sudo apt-get install'
alias remove='sudo apt-get remove'
alias update='sudo apt-get update'
alias upgrade='sudo apt-get update && sudo apt-get upgrade'

# Power
alias reboot="sudo shutdown -r now"
alias off="sudo shutdown -h now"

# Some random aliases
alias cls=clear # more cmd style alias
alias reload='source ~/.bashrc' #reloads .bashrc

#functions

psgrep() {
	if [ ! -z $1 ] ; then
		echo "Grepping for processes matching $1..."
		ps aux | grep $1 | grep -v grep
	else
		echo "!! Need name to grep for"
	fi
}


extract () {
   if [ -f $1 ] ; then
       case $1 in
           *.tar.bz2)   tar xvjf $1    ;;
           *.tar.gz)    tar xvzf $1    ;;
           *.bz2)       bunzip2 $1     ;;
           *.rar)       unrar x $1       ;;
           *.gz)        gunzip $1      ;;
           *.tar)       tar xvf $1     ;;
           *.tbz2)      tar xvjf $1    ;;
           *.tgz)       tar xvzf $1    ;;
           *.zip)       unzip $1       ;;
           *.Z)         uncompress $1  ;;
           *.7z)        7z x $1        ;;
           *)           echo "don't know how to extract '$1'..." ;;
       esac
   else
       echo "'$1' is not a valid file!"
   fi
 }
 
 #cd .. n times
 function cdn(){ for i in `seq $1`; do cd ..; done;}
 
#create new branch from master
function newbranch(){
    git checkout master
    git pull
    git checkout -b $1
    git push origin $1
    git branch --set-upstream-to=origin/$1
    git branch
}


alias psg="ps aux | grep -v grep | grep -i -e VSZ -e"

