<?php

if ($_SERVER["REQUEST_METHOD"] == "POST") {
  
        
        $main=$_POST['main'];
        $drinks=$_POST['drinks'];
		$sum=0;

	
	echo "<h1 style=\"color:#00008B\">Your Order is Successful!! </h1><br><br>";

	echo "<h2 style=\"color:#00008B\">Selected Items </h2>";
	
		
		    if (isset($main) && $main=="ham") 
	          {echo "Hamburger-$6.25";
				$sum+=6.25;}
	        else if (isset($main) && $main=="pizza") 
	          {echo "Pizza-$5.95";
				$sum+=5.95;}
		    else if (isset($main) && $main=="salad") 
	          {echo "Salad-$4.95";
				$sum+=4.95;}
            else if (isset($main) && $main=="sausage") 
	          {echo "Sausage Sandwich-$10.20";
				$sum+=10.20;}
	        else if (isset($main) && $main=="bf") 
	          {echo "Grilled Breakfast Wrap-$12.45";
				$sum+=12.45;}
            else if (isset($main) && $main=="donut") 
	          {echo "Apple Fritter Donuts-$5.50";
				$sum+=5.50;}
		  
	echo "<br>";	  
		

		    if(!empty($_POST['item'])) {    
			foreach($_POST['item'] as $value){
				echo $value;
				$sum+=0.75;
                echo "<br>";}
				
			}

			if(!empty($_POST['drinks'])) {    
			foreach($_POST['drinks'] as $value){
					echo $value;
					$sum+=1.50;
                    echo "<br>";}
					

    echo "<h1 style=\"color:#00008B\">************************ </h1><br>";
				}
    echo "Total Amount for Selected Items:$".$sum;
    echo "<br>";

						
			if(!empty($_POST['tips'])) {    
			foreach($_POST['tips'] as $value){
						echo "Tips Percentage:".$value;
						if(strcmp($value,"10%")==0)
						{
							$sum-=(($sum*10)/100);
						}
						else if(strcmp($value,"15%")==0)
						{
							$sum-=(($sum*15)/100);
						}
						else if(strcmp($value,"20%")==0)
						{
							$sum-=(($sum*20)/100);
						}
						
					}
				}
        echo "<br><br>";

				$tax=(($sum*7.75)/100);
				$total=$sum+$tax;
		}

		
	
?>

<!DOCTYPE html>

<html>

 <head>
  <style>
         
   .button{           
     background-color: #00008B;
     color: white;
     padding: 10px 20px;
     text-align: center;
     font-size: 16px;

         }
  </style>
    <link rel="stylesheet" type="text/css" href="main.css" />
</head>

<body>

<form action="ResturantMenu.html" method= "post">
   <div id = "content">

      <h1>Order Total</h1>
     
      <label>Subtotal:</label>
      <span><?php echo "$".$sum; ?></span><br>

      <label>Tax(7.75%):</label>
      <span><?php echo "$".$tax  ?></span><br>
	
	  <label>Order Total:</label>
      <span><?php echo"$".$total; ?></span><br>
	  

    </div>

    <div id="button">
        <br><br>

       <input type="submit" class="button"value="Exit"/><br>

    </div>

</form>
</body>
</html>