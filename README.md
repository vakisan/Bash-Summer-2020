# Command Line Codecademy Summer 2020

pwd - print working director
ls - list files and directories in current file
cd - change directory
mkdir - make directory in current directory
touch - creates a new file inside the working directory

cd.. - goes back one directory
touch newfile.md - new file created in working directory with extention md

Bash - Bourne Again SHell is a Command Line Interface (CLI) created by Brian Fox.
shell is a special type of CLI

to create a file AND add a line to the file we use:
echo "Hello Command Line" >> nameofFile.extension // I have used echo in PHP and I assume it may have the same role here.

to see the content of the file:
cat filename - will output content of filename.
cat filnamee>filename2 - will overwrite the file2.
cat filename1 filename2 - will output both filename1 and filename2 one after the other.
cat -n filename - -n formats the output to show line numbers.
cat >newfile - create a new file.
cat [fileName] > [destination file name].
cat file1 >> file2 - appends content of file 2 to file 1.
tac filename will reverse content of file.
...more

ls
ls -a - will also show files which are hidden ie starting with . -a etc... are called options.
ls -l -lists all content in long format. this will return a table format result. it will present the access right, quantify the hard links which indicates the number of child files, the username of the file owner, the group that owns the file, size of file, modified, and name of file/directory.
ls -t lists all content in order they were last modified.
ls -alt - runs all three options together.

cp - copy file into another file. need file1 and file 2 listed oneafter the other with a space. to copy a file from one directory to another we need to state the file and then state which directory to copy to.

cp * directory - to copy all in current directory to directory atgument.
cp letter* directory- top copy all in current ddirectory that start with letter.

mv - moves files
mv argument1 argument2... destination - moves argumentfiles to destination.
mv can also be used to rename files
mv filenameold filenamenew - if no destination given the filenameold gets moved into filenamenew.

rm - removes files from directory
rm filename - removes filename.
rm -r directory - removes the directory and its children.
rm -rf removes all subfiles and f for ignoring non-existant files.
rm directory/* - removes all in directpry specified.

echo "value" will take "value" as a standard input and eachoes the string "value" back as a standard output. standard input is input from input device (stdin) standard outupt is stdout and error output are stder.
echo " " > filename - this will redirect the stdin to the filename speicified. 

">" redirects output to destination
">>" redirects output to destination and appends instead of overwritting.
"<"  redirect output to the left. NEED TO READ MORE ON THIS!cta
 "|" is a pipe. it takes the output of the command on the left and pipes it as the standard input to the command on the right.
 "| wc" pipes the left command to the wc command.
sort - command is used to sort the input of file for the outputsort. this can be combined with | to use this output as input.

uniq - is used to filter out adjacent dusplicates in a file 
if you wished to remove all duplicates even if not adjacent then we could sort and then run uniq. to do this in one go. sort file | uniq > outputtonewFile. if wanting to store this.

grep "value" filename - stands for global regular expression print. it looks for lines that match a pattern with case-sensitivity and it returns the results.
grep -i - is used to remove case-senstivity option.
grep -R "value" directory - is used to search within a directory for the regular expression. it returns the output lines and filenames.
grep -Rl "value directory - will not output the occurence and only give filennames in driectory R mean recursive

sed - stream editor to replace input using expressions
sed "s/string/rain/g" filename - s stands for substitution. this expression will substritute, string occurence with rain occurences.

wc - word count command
wc -l - lines returned.

## Storing Environment Settings

nano filename - creates a file and opens up the nano text editor.
nano editor commands are at the bottom arrow up is control key.
very simple to use.
alias can be used to set alternate keys for calling commands in bash.
to print history we normally call history. but if the bash profile has code that sets a shorcut as " alias hh="history". then after activating this using source command in bash you should be able to use hh shortcut to call history.
source ~/.bash_profile - used to activate the bash profile edits.

~/.bash_profile - is used to store environment settings. this is called the bash profile. When loading bash it will run this command before executing commands.
~ is the user home directory
/ for sub directory.
. for hidden file with name bash_profile.

history - command to obtain history
echo command can be added to a bash script
export USER ="user name" and when this is activated with source we can call echo $USER to prin the value given.

environment varibles USER exists and can be set using nano on bash profile file. Normally, this is set to the computers's owener name.

export - make the variable available to the all child sessions from which we initiated from the current session. this allows varaibles to persist across programs.

when returning variable values in bash, $ is always used in the name of the vairable start.

PS1 is an environment variable in bash we have $ uatomatically set. However, this can be changed by assigning a new value to PS1.

$HOME is the variable that stores the home directory.
home directory can be customised as before. 

$PATH lists all the directories that contain scripts separated by :
these scripts are the ones that contain the commands like ls, pwd cat... we can specify the bin/pwd and it will still run pwd script.

env - returns all the enviroment variables.
env | grep PATH - eg applied from before can be used to find the variable path in the output.

date is another command that will print date and time and zone in bash

less- is a command that is an alternative to cat but is better adapted to handle larger files. it will show only one page at a time
less -N will also show line numbers
q to quit less

to activate changes int bash profile we can also restart a new terminal session.

## BASH Scripting

bash scripting can help make devlopment faster by creating scripts to create commands that run frequent tasks take much less time.

convention for bash scripting must start with:
#!/bin/bash - on its own line this tells which interpreter to use. the files should conveionally be stored in bin directory as that is the common place for commly used scripts to be found.

scripts must have permissiont o execute.
on startup terminal will run ~/.bashrc and on OSX, this is ~/.bash_profile.

to ensure that the scripts in /bin/ are available, we need to add this directory to PATH variable within the bash profile file.

to run a script in bin folder use ./scriptname.sh
variable names can be added to the script. to acess the value of variable name we must preppend a $.
else if simply recalling the value in code we do not need to do this.

Conditionals
Numeric comparisons - conditional operators in bash are two letter shortcuts. x operator y 
"<" = -lt
">" = -gt
">="= -ge
"<=" = -le
is null = -z
"==" = -eq
"!=" = -nq

to compare strings we use == and !=

NOTE: unlike in java there is an explicit then to represent the {} equivalent.
space aroud commands are very important. Otherwise a different command will be run.
" [ "  and " ] " at start and end of brackets respectively.

aithmetic operations in bash take this form:
variableWithout$ = $((variablewithout$+1)) to self increment.

if statements requires 3 parts
if [ i -lt j ] 
then
    //code
else
    //code
fi 
fi must be added as if signals the end of the if statement.

for loops require
word = //assignment
for word in $list
do
    //code
done

while and until loops
while [ x -lt y ]
do
    //code
done

until [ x -lt y ]
do
    //code
done

User Input
to get input from the user we use the read command
read number //no $ as there is no need to access the variable when setting it.

another way to get user input is to run input upon calling the script in command line.
this is simialr to java running args when running program.
argumuments must be separated with space.
to access the inputs from the script side, they are stored in $1 $2 ....
if infinite number is required then we can reference these using $@.
loops are likely to be required to read inputs

to acess external files, we can create a variable to store the files in a directory and maybe iterate throught them. use * to select all files.

to make it easier to run scripts we can use aliases. this will enable us to create short form commands to run a script, we can also pass command line arguments automatically too.
this is done:
alias shortcut='./scriptFileName.sh "value1" "value2"'
//use different quotations.

to add alias we could add to ~/.bash_profile or we could add alias using the command line as above.

## extra commands

head options files - this will return the first 10 lines of the provided filename.
head -n - to specify the number of lines desired. ie -n4 = 4lines or we could use only number also.
head -c - to specify the number of bytes from start of file to return. add k to multipley cnumber by 1024. or m

read -a splits an input into an array of words. words have space around them