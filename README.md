#!/bin/bash
####!/bin/awk -f

#----------------------------
#Comment
#-----------------------------

#Author: Ann Wyers (wyersa@student.ncmich.edu)
#Version: 12.17.2019
#Purpose: Project 6

# Bash Menu Script Example

#-----------------------------
# Define variables
#-----------------------------
IFS=","
declare inFile="$1"
declare outFile="$2"
declare -a LName
declare -a FName
declare -a Age
declare -A People

#-----------------------------
# Dispatch
#-----------------------------

main(){
        readFile
        populateFName
        printFName
        populateLName
        printLName
        populateAge
        printAge
        exit 0
}

#------------------------------
# Methods/Functions/Subroutines
#------------------------------

readFile(){
#    while read LName FName SAddress City State Zip; do
#        printf " ${LName} ${FName} ${SAddress} ${City} ${State} ${Zip}\n"
    declare -i lineNumber=0
    while read LName FName Age;
    do
          LName[$lineNumber]=$LName
          FName[$lineNumber]=$FName
          Age[$lineNumber]=$Age
          printf " ${LName} ${FName} ${Age}\n"
    done < HospitalEmployees1.csv
 }


# v works v kind of cool
#while IFS=, read -r col1 col2
#do
#        echo "I got:$col1|$col2"
#    done < HospitalEmployees1.csv

#awk version 4.0.2 
#awk -F',' '{print $1}' HospitalEmployees1.csv
#awk -F',' '{print $2}' HospitalEmployees1.csv
#awk -F',' '{print $3}' HospitalEmployees1.csv

populateFName (){
    IFS=$'\n'
    FName=($(awk -F',' '{print $2}' HospitalEmployees1.csv))
#unset IFS < doesn't work
}

printFName (){
echo ${FName[@]}
}

populateLName (){
    IFS=$'\n'
    LName=($(awk -F',' '{print $1}' HospitalEmployees1.csv))
    }

printLName (){
echo ${LName[@]}
}


populateAge (){
    IFS=$'\n'
    Age=($(awk -F',' '{print $3}' HospitalEmployees1.csv))
    }

printAge (){
echo ${Age[@]}
}

#ssAge()

#declare -i Age=($(awk -F',' '{print $3}' HospitalEmployees1.csv))
#echo ${Age[@]}

#awk -F',' if $3>62 {print $3}' HospitalEmployees1.csv | wc -l

declare -i count
#IFS=","
IFS=$'\n'
Age=($(awk -F',' '{print $3}' HospitalEmployees1.csv))
echo ${Age[@]}
#if  [ $Age -gt 62 ]  ; 
#    then
#        echo ok
#    else
#        echo bad
#fi
#
#if [ $Age -gt 62 ] ;
#    then 
#        (( count++ ))
#        echo $count
#     else
#        counter=0
# fi
 
#while read -r count age; do
#      if test "$Age" -gt 65; then   
#         echo "There are "$count" employees that can retire"
#      fi   
#done < HEage

#for i in ${Age[@]}
#do
#    echo "Employee is $i "
#done
 

#while (( ${Age[@]} > 62 ))
#do 
#    echo -e "${Age[@]} \c"
#    sleep 1
#done




    
    
    
    main
