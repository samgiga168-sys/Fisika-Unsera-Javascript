<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TOEFL Score Calculator</title>
    <link href="css/bootstrap.min.css" rel="stylesheet">
    <script id="MathJax-script" async src="math.js"></script>
    <style>
        body {
            background-image: url('background.jpg'); /* Add a background image */
            background-size: cover;
            background-attachment: fixed;
            color: #ffffff; /* Change the text color for better contrast */
        }
        .card {
            background-color: rgba(0, 0, 0, 0.8); /* Dark transparent background for the card */
            border-radius: 15px; /* Rounded corners for the card */
            color: #ffffff;
        }
        .form-label {
            font-weight: bold;
        }
        .btn-primary {
            background-color: #007bff;
            border: none;
            border-radius: 10px; /* Rounded button */
        }
        .btn-primary:hover {
            background-color: #0056b3; /* Darker shade on hover */
        }
        .badge {
            font-size: 1.5rem;
        }
    </style>
</head>
<body>

<div class="container mt-5">
    <div class="row justify-content-center">
        <div class="col-lg-6">
            <div class="card shadow-lg">
                <div class="card-body p-5">
                    <h2 class="text-center mb-4">TOEFL Score Calculator</h2>
                    
                    <form method="POST" action="">
                        <div class="mb-4">
                            <label for="raw1" class="form-label">Raw Score Section 1 (Listening Comprehension):</label>
                            <input type="number" id="raw1" name="raw1" class="form-control form-control-lg">
                        </div>

                        <div class="mb-4">
                            <label for="converted1" class="form-label">Converted Score Section 1:</label>
                            <input type="number" id="converted1" name="converted1" class="form-control form-control-lg" required>
                        </div>

                        <div class="mb-4">
                            <label for="raw2" class="form-label">Raw Score Section 2 (Structure and Written Expression):</label>
                            <input type="number" id="raw2" name="raw2" class="form-control form-control-lg">
                        </div>

                        <div class="mb-4">
                            <label for="converted2" class="form-label">Converted Score Section 2:</label>
                            <input type="number" id="converted2" name="converted2" class="form-control form-control-lg" required>
                        </div>

                        <div class="mb-4">
                            <label for="raw3" class="form-label">Raw Score Section 3 (Reading Comprehension):</label>
                            <input type="number" id="raw3" name="raw3" class="form-control form-control-lg">
                        </div>

                        <div class="mb-4">
                            <label for="converted3" class="form-label">Converted Score Section 3:</label>
                            <input type="number" id="converted3" name="converted3" class="form-control form-control-lg" required>
                        </div>

                        <div class="d-grid">
                            <button type="submit" name="submit" class="btn btn-primary btn-lg">Calculate TOEFL Score</button>
                        </div>
                    </form>

                    <?php
                    if ($_SERVER["REQUEST_METHOD"] == "POST") {
                        $converted1 = $_POST['converted1'];
                        $converted2 = $_POST['converted2'];
                        $converted3 = $_POST['converted3'];

                        // Calculate total score
                        $totalScore = $converted1 + $converted2 + $converted3;

                        // Calculate average score
                        $averageScore = $totalScore / 3;

                        // Calculate final TOEFL score
                        $finalScore = $averageScore * 10;
                        $finalScore = round($finalScore);

                        // Convert final TOEFL score to 1-100 scale
                        $scaledScore = ($finalScore / 300) * 100;
                        $scaledScore = round($scaledScore);

                        echo "<h3 class='text-center mt-4'>Your Total TOEFL Score is: <span class='badge bg-success'>$finalScore</span></h3>";

                        // Displaying MathJax formula
                        echo "
                        <p class='text-left mt-3'>\\(\\text{Total Score} = $converted1 + $converted2 + $converted3 = $totalScore\\)</p>
                        <p class='text-left'>\\(\\text{Average Score} = \\frac{{$totalScore}}{3} = $averageScore\\)</p>
                        <p class='text-left'>\\(\\text{Final TOEFL Score} = $averageScore \\times 10 = $finalScore\\)</p>
                        <p class='text-left'>\\(\\text{Converted Score on a 1-100 Scale} = \\frac{{$finalScore}}{300} \\times 100 = $scaledScore\\)</p>
                        ";
                    }
                    ?>
                </div>
            </div>
        </div>
    </div>
</div>

<script src="js/popper.min.js"></script>
<script src="js/bootstrap.min.js"></script>

<div class="py-md-3">

</div>
</body>
</html>
