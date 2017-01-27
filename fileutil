package cst8284.quizMaster;

/* File Name: FileUtils.java
Author: Dave Houtman/Zhen Qu 040587623
Course: CST8132-OOP
Assignment: 3
Date: December 07, 2016
Professor: Dave Houtman
Purpose: Open a .quiz file and load questions to a QA type ArrayList */

import javafx.stage.Stage;
import javafx.stage.FileChooser;
import javafx.stage.FileChooser.ExtensionFilter;
import java.io.EOFException;
import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.util.ArrayList;

/**
 * open a .quiz file by FileChooser and load the questions to a QA type ArrayList
 * @author Zhen Qu
 * @version 2.0
 * @see javafx.stage.Stage, javafx.stage.FileChooser, javafx.stage.FileChooser.ExtensionFilter, java.io.EOFException, java.io.File, java.io.FileInputStream, java.io.IOException, java.io.ObjectInputStream, java.util.ArrayList 
 * @since javac 1.8.0_102, java 1.8.0_111
 */
public class FileUtils {
   /**
    * QuizFileAbsolutePathAndName - a String type field to store the absolute path of .quiz file
    */
   private static String QuizFileAbsolutePathAndName="";
   /**
    *{@value} ON, OFF - two static boolean to control the loop
    */
   public final static boolean ON = true, OFF = false;
	
   public static File getFileHandle(Stage primaryStage){
	  FileChooser fc = new FileChooser();
	  fc.setTitle("Open Quiz File");
	  fc.getExtensionFilters().addAll(
	      new ExtensionFilter("Quiz Files", "*.quiz"),
	      new ExtensionFilter("All Files", "*.*"));
		 
	  File quizFile = fc.showOpenDialog(primaryStage);
	  
	  setFileName(quizFile);
	  return(quizFile);
   }
   
   /**
    * getQAArray() to load a .quiz file to a QA type Arraylist
    * @param absPath String type field to pass the absolute path of .quiz file
    * @return Arraylist a QA type Arraylist of questions
    */
   public static ArrayList<QA> getQAArray(String absPath){

	   ArrayList <QA> qaArray = new ArrayList <>();         //initiate a QA type ArrayList 
	   try{
			      FileInputStream objectFileStream =  
			       new FileInputStream(absPath);            //Open the file as a FileInputStream and load the first numObjects into a                                     
			      ObjectInputStream ois =                   //new Array of type QA. Then return an array of QA objects to the caller
				   new ObjectInputStream(objectFileStream);
			      boolean check=true;                       //a boolean field to control the while loop to load .quiz file to ArrayList
			      while (check) {
			  try{
			  qaArray.add((QA) ois.readObject());
			  
			  }catch(EOFException ex){                     //EOFException to tell if the .quiz file loaded completely
			       check=false;
			  }catch(NullPointerException ex){             //NullPointerException to signal if a QA object is set to null
				   QuizMain.showAlert("NullPointerException Error Caught!", "NullPointerException");
			  }
				 }
			       ois.close();
	   	}catch(IOException e){							   //IOException to signal if some sort of I/O exceptions occured
			 e.printStackTrace();
		} catch (ClassNotFoundException e1) {              //Auto-generated catch block
			 e1.printStackTrace();
		   }finally{
		   	}
	   return (qaArray);
   }
    
   private static void setFileName(File f) {
	   QuizFileAbsolutePathAndName = (FileExists(f))? f.getAbsolutePath():"";
   }
   
   public static String getFileName(){
	   return QuizFileAbsolutePathAndName;
   }
   
   public static String getFileName(File f){
	   return f.getAbsolutePath();
   }
   
   public static Boolean FileExists(File f){
	   return (f!=null && f.exists() && f.isFile() && f.canRead());
   }
   
   public static void waitAndShow(boolean b){
	   while(b){};  // loop until b is OFF
   }
      
}
